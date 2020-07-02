---
title: 2. Inizializzazione del progetto e prima applicazione
description: Parte 2 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345731"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inizializzazione del progetto e prima applicazione

## <a name="overview"></a>Panoramica

In questa prima esercitazione inizierai a creare una nuova applicazione Unreal per HoloLens 2. Eseguirai varie operazioni, come aggiungere il plug-in HoloLens, creare e illuminare un livello e popolarlo con una scacchiera e un pezzo degli scacchi. Non dovrai modellare nulla da zero perché userai asset predefiniti per il pezzo degli scacchi 3D e i materiali degli oggetti. Al termine di questa esercitazione avrai un'area di disegno vuota pronta da configurare per la realtà mista.

Prima di proseguire, assicurati di disporre di tutti i prerequisiti indicati nella [Guida introduttiva](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).

## <a name="objectives"></a>Obiettivi
* Configurazione di un progetto Unreal per lo sviluppo con HoloLens
* Importazione di asset e configurazione di una scena
* Creazione di attori ed eventi a livello di script con progetti

## <a name="creating-a-new-unreal-project"></a>Creazione di un nuovo progetto Unreal
Prima di tutto, è necessario un progetto su cui lavorare. Se è la prima volta che crei un'app Unreal per HoloLens, dovrai [scaricare i file di supporto](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) dal launcher Epic.

1. Avvia Unreal Engine

2. Seleziona **Games** (Giochi) in **New Project Categories** (Categorie nuovo progetto) e fai clic su **Next** (Avanti). 

![Selezionare il modello di progetto Games (Giochi)](images/unreal-uxt/2-gamestemplate.png)

3. Seleziona il modello **Blank** (Vuoto) e fai clic su **Next** (Avanti). 

![Selezionare il modello vuoto](images/unreal-uxt/2-template.PNG)

4. Imposta **C++** , **Scalable 3D or 2D, Mobile/Tablet** (3D o 2D scalabile, Cellulare/Tablet) e **No Starter Content** (Nessun contenuto iniziale) in **Project Settings** (Impostazioni progetto). 
    * Scegli una posizione di salvataggio e fai clic su **Create Project** (Crea progetto). 

> [!NOTE]
> Devi selezionare un progetto C++ anziché un progetto Blueprint per compilare il plug-in UX Tools, che verrà configurato più avanti nella sezione 4.

![Impostazioni iniziali del progetto](images/unreal-uxt/2-project-settings.PNG)

Il progetto dovrebbe aprirsi automaticamente nell'editor Unreal e a quel punto puoi passare alla sezione successiva.

## <a name="enabling-required-plugins"></a>Abilitazione dei plug-in necessari
Prima di iniziare ad aggiungere oggetti alla scena, è necessario abilitare due plug-in.

1. Apri **Edit > Plugins** (Modifica > Plug-in) e seleziona **Augmented Reality** (Realtà aumentata) nell'elenco di opzioni predefinite. 
    * Scorri verso il basso fino a **HoloLens** e seleziona **Enabled** (Abilitato). 

![Abilitazione dei plug-in HoloLens](images/unreal-uxt/2-plugins.PNG)

2. Seleziona **Virtual Reality** (Realtà virtuale) nell'elenco di opzioni predefinite. 
    * Scorri verso il basso fino a **Microsoft Windows Mixed Reality**, seleziona **Enabled** (Abilitato) e riavvia l'editor. 

![Abilitazione del plug-in Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> Per lo sviluppo di HoloLens 2 sono necessari entrambi i plug-in.

Terminata questa configurazione, puoi iniziare a creare altri livelli.

## <a name="creating-a-level"></a>Creazione di un livello
L'attività successiva consiste nel creare una semplice configurazione di gioco con un punto iniziale e un cubo per riferimento e scala.

1. Seleziona **File > New Level** (File > Nuovo livello) e scegli **Empty Level** (Livello vuoto). In questa fase, la scena predefinita nel riquadro di visualizzazione dovrebbe essere vuota.

2. Seleziona **Basic** (Base) nella scheda **Modes** (Modalità) e trascina **PlayerStart** nella scena. 
    * Imposta **Location** (Posizione) su **X = 0**, **Y = 0** e **Z = 0** nella scheda **Details** (Dettagli). L'utente viene posizionato al centro della scena all'avvio dell'app.

![Riquadro di visualizzazione con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. Trascina un oggetto **Cube** (Cubo) dalla scheda **Basic** (Base) nella scena. 
    * Imposta **Location** (Posizione) su **X = 50**, **Y = 0** e **Z = 0**. Il cubo viene posizionato a 50 cm di distanza dal giocatore al momento dell'avvio. 
    * Imposta **Scale** (Scala) su **X = 0.2**, **Y = 0.2** e **Z = 0.2** per ridurre le dimensioni del cubo. 

Il cubo non sarà visibile finché non aggiungerai una luce alla scena, che è l'ultima attività da eseguire prima di testare la scena.

4. Passa alla scheda **Lights** (Luci) nel pannello **Modes** (Modalità) e trascina un oggetto **Directional Light** (Luce direzionale) nella scena. Posiziona la luce al di sopra di **PlayerStart** perché sia visibile.

![Riquadro di visualizzazione con aggiunta di luce](images/unreal-uxt/2-light.PNG)

5. Passa a **File > Save Current** (File > Salva corrente), assegna il nome **Main** (Principale) al livello e fai clic su **Save** (Salva). 

Una volta impostata la scena, seleziona **Play** (Riproduci) sulla barra degli strumenti per vedere il cubo in azione. Quando avrai terminato di ammirare il tuo lavoro, premi **ESC** per arrestare l'applicazione.

![Un cubo nel riquadro di visualizzazione](images/unreal-uxt/2-cube.PNG)

Ora che la scena è configurata, puoi iniziare ad aggiungere la scacchiera e il pezzo per completare l'ambiente dell'applicazione.

## <a name="importing-assets"></a>Importazione di asset
Al momento la scena è un po' spoglia, ma puoi arricchirla importando asset predefiniti nel progetto.

1. Scarica e decomprimi la cartella di asset [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).

2. Fai clic su **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegna il nome **ChessAssets** alla cartella. 
    * Fai doppio clic sulla nuova cartella, in cui importerai gli asset 3D.

![Visualizzare o nascondere il pannello delle origini](images/unreal-uxt/2-showhidesources.PNG)

3. Fai clic su **Import** (Importa) in **Content Browser** (Browser contenuto), seleziona tutti gli elementi nella cartella di asset decompressa e scegli **Open** (Apri). 
    * Questa cartella contiene le mesh degli oggetti 3D per la scacchiera e i pezzi in formato FBX e le mappe di texture in formato TGA che userai per i materiali.  

4. Quando viene visualizzata la finestra FBX Import Options (Opzioni di importazione FBX), espandi la sezione **Material** (Materiale) e modifica **Material Import Method** (Metodo importazione materiale) in **Do Not Create Material** (Non creare materiale).
    * Fai clic su **Import All** (Importa tutto).

![Opzioni importazione FBX](images/unreal-uxt/2-nocreatemat.PNG)

Non serve fare altro per gli asset. Il prossimo set di attività consiste nel creare i blocchi predefiniti dell'applicazione con i progetti.

## <a name="adding-blueprints"></a>Aggiunta di progetti

1. Fai clic su **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) in **Content Browser** (Browser contenuto) e assegna il nome **Content Browser** (Browser contenuto) alla cartella. 

> [!NOTE]
> I [progetti](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) sono asset speciali che forniscono un'interfaccia basata su nodi per la creazione di nuovi tipi di attori ed eventi a livello di script. 

2. Fai doppio clic nella cartella **Blueprints** (Progetti), quindi fai clic con il pulsante destro del mouse e scegli **Blueprint Class** (Classe progetto).         
    * Seleziona **Actor** (Attore) e assegna al nuovo progetto il nome **Board** (Tavola). 

![Selezionare una classe padre per il progetto](images/unreal-uxt/2-bpparent.PNG)

Il nuovo progetto **Board** (Tavola) verrà incluso nella cartella **Blueprints** (Progetti) mostrata nello screenshot seguente. 

![Nuovo progetto Board (Tavola)](images/unreal-uxt/2-bpboard.PNG)

È tutto pronto per iniziare ad aggiungere materiali agli oggetti creati.

## <a name="working-with-materials"></a>Uso dei materiali
Gli oggetti che hai creato sono grigi per impostazione predefinita e questo non li rende particolarmente gradevoli dal punto di vista estetico. L'ultima serie di attività di questa esercitazione consiste appunto nell'aggiungere materiali e mesh agli oggetti.

1. Fai doppio clic su **Board** (Tavola) per aprire l'editor dei progetti. 

2. Fai clic su **Add Component > Scene** (Aggiungi componente > Scena) nel pannello **Components** (Componenti) e assegna il nome **Root** (Radice) alla scena. Nota che **Root** (Radice) viene visualizzato come elemento figlio di **DefaultSceneRoot** nello screenshot seguente:

![Sostituzione della radice](images/unreal-uxt/2-root-blueprint.PNG)


3. Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituire la radice ed eliminare la sfera nel viewport. 

![Sostituzione della radice](images/unreal-uxt/2-root.PNG)


4. Fai clic su **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) nel pannello **Components** (Componenti) e assegna il nome **SM_Board** (MS_Tavola) alla mesh statica. Verrà visualizzata come oggetto figlio in **Root** (Radice).

![Aggiunta di una mesh statica](images/unreal-uxt/2-sm-board.PNG)

4. Fai clic su **SM_Board** (MS_Tavola), scorri verso il basso fino alla sezione **Static Mesh** (Mesh statica) del pannello **Details** (Dettagli) e quindi seleziona **ChessBoard** (Scacchiera) nell'elenco a discesa. 

![Mesh Tavola nel riquadro di visualizzazione](images/unreal-uxt/2-sm-board-view.PNG)

5.  Sempre nel pannello **Details** (Dettagli) espandi la sezione **Materials** (Materiali) e fai clic su **Create New Asset > Material** (Crea nuovo asset > Materiale) nell'elenco a discesa. 
    * Assegna a questo materiale il nome **M_ChessBoard** (M_Scacchiera) e salvalo nella cartella **ChessAssets**. 

![Creare un nuovo materiale](images/unreal-uxt/2-newmat.PNG)

6.  Fai doppio clic sull'immagine del materiale **M_ChessBoard** (M_Scacchiera) per aprire l'editor dei materiali. 

![Aprire l'editor dei materiali](images/unreal-uxt/2-material-editor.PNG)

7. Nell'editor dei materiali fai clic con il pulsante destro del mouse e cerca **Texture Sample** (Esempio di texture). 
    * Espandi la sezione **Material Expression Texture Base** (Espressione materiale - Base texture) nel pannello **Details** (Dettagli) e imposta **Texture** su **ChessBoard_Albedo** (Scacchiera_Albedo). 
    * Trascina il segnaposto di output **RGB** sul segnaposto Base Color (Colore di base) di **M_ChessBoard** (M_Scacchiera). 

![Impostare il colore di base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Ripeti altre quattro volte il passaggio precedente per creare altri quattro nodi **Texture Sample** (Esempio di texture) con le impostazioni seguenti:
    * Imposta **Texture** su **ChessBoard_AO** (Scacchiera_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).
    * Imposta **Texture** su **ChessBoard_Metal**(Scacchiera_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico). 
    * Imposta **Texture** su **ChessBoard_Normal** (Scacchiera_Normale) e collega **RGB** al segnaposto **Normal** (Normale).
    * Imposta **Texture** su **ChessBoard_Rough**(Scacchiera_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza). 
    * Fare clic su **Save**. 

![Associare le texture rimanenti](images/unreal-uxt/2-boardmat.PNG)

Prima di continuare, verifica che la configurazione del materiale corrisponda allo screenshot riportato sopra.

## <a name="populating-the-scene"></a>Popolamento della scena
Se torni al progetto **Board** (Tavola), noterai che il materiale appena creato è stato applicato. A questo punto devi solo configurare la scena. Prima di tutto, modifica le proprietà seguenti per assicurarti che la scacchiera sia di dimensioni ragionevoli e disposta nella corretta angolazione quando viene inserita nella scena:
1.  Imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**. 
    * Fai clic su **Compile** (Compila) sulla barra degli strumenti in alto, quindi su **Save** (Salva) e torna alla finestra principale. 

![Scacchiera con materiale applicato](images/unreal-uxt/2-chessboard.PNG)

2.  Fai clic con il pulsante destro del mouse su **Cube > Edit > Delete** (Cubo > Modifica > Elimina) e trascina **Board** (Tavola) da **Content Browser** (Browser contenuto) nel viewport. 
    * Imposta **Location** (Posizione) su **X = 80**, **Y = 0** e **Z = 20**. 

3.  Fai clic sul pulsante **Play** per visualizzare la nuova tavola nel livello. Premi **ESC** per tornare all'editor. 

A questo punto creerai un pezzo degli scacchi seguendo la stessa procedura usata per la scacchiera:

1. Passa alla cartella **Blueprints** (Progetti), fai clic con il pulsante destro del mouse e scegli **Blueprint Class** (Classe progetto) e **Actor** (Attore). Assegna a questo attore il nome **WhiteKing** (Re bianco).

2. Fai doppio clic su **WhiteKing** per aprirlo nell'editor progetti, fai clic su **Add Component > Scene** (Aggiungi componente > Scena) e assegna il nome **Root** (Radice) alla scena. 
    * Trascina **Root** (Radice) su **DefaultSceneRoot** per sostituirla. 

3. Fai clic su **Add Component > Static Mesh** (Aggiungi componente > Mesh statica) e assegna il nome **SM_King** (MS_Re) alla mesh. 
    * Nel pannello Details (Dettagli) imposta **Static Mesh** (Mesh statica) su **Chess_King** (Scacchi_Re) e **Material** (Materiale) su un nuovo materiale denominato **M_ChessWhite** (M_ScacchiBianco). 

4. Apri **M_ChessWhite** (M_ScacchiBianco) nell'editor dei materiali e associa i seguenti nodi **Texture Sample** (Esempio di texture) a quanto segue:
    * Imposta **Texture** su **ChessWhite_AO** (ScacchiBianco_OA) e collega **RGB** al segnaposto **Ambient Occlusion** (Occlusione ambiente).
    * Imposta **Texture** su **ChessWhite_Metal**(ScacchiBianco_Metallo) e collega **RGB** al segnaposto **Metallic** (Metallico). 
    * Imposta **Texture** su **ChessWhite_Normal** (ScacchiBianco_Normale) e collega **RGB** al segnaposto **Normal** (Normale).
    * Imposta **Texture** su **ChessWhite_Rough**(ScacchiBianco_Ruvido) e collega **RGB** al segnaposto **Roughness** (Ruvidezza). 
    * Fare clic su **Save**. 

Prima di continuare, il materiale **M_ChessKing** (M_ScacchiRe) deve essere simile all'immagine seguente.

![Creare il materiale per il re degli scacchi](images/unreal-uxt/2-chesskingmat.PNG)

Hai quasi finito: ora basta aggiungere il nuovo pezzo degli scacchi alla scena: 

1. Apri il progetto **WhiteKing** (ReBianco) e imposta **Scale** (Scala) su **(0.05, 0.05, 0.05)** e **Z Rotation** (Rotazione Z) su **90**.
    * Compila e salva il progetto e quindi torna alla finestra principale. 

2.  Trascina **WhiteKing** (ReBianco) nel viewport, passa al pannello **World Outliner** (Delinatore mondo reale) e trascina **WhiteKing** (ReBianco) su **Board** (Tavola) per renderlo un oggetto figlio.

![Delineatore mondo reale](images/unreal-uxt/2-child.PNG)

3.  Nel pannello **Details** (Dettagli) in **Transform** (Trasformazione) imposta **Location** (Posizione) di **WhiteKing** (ReBianco) su **X = -26**, **Y = 4** e **Z = 0**.

Ecco fatto! Fai clic su **Play** (Riproduci) per vedere in azione il livello popolato, quindi premi **ESC** quando vuoi uscire. In questa esercitazione sono stati illustrati molti aspetti relativi alla creazione di un progetto semplice, ma il tuo progetto ora è pronto per passare alla parte successiva della serie, dedicata alla configurazione per la realtà mista. 

[Sezione successiva: 3. Configurare il progetto per la realtà mista](unreal-uxt-ch3.md)
