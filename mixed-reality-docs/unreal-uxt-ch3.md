---
title: 3. Configurazione del progetto per la realtà mista
description: Parte 3 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: f79985b2ce9e26971c23acf36a3538bf7f3c166e
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84879545"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configurazione del progetto per la realtà mista

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente ti sei dedicato alla configurazione del progetto dell'app di scacchi. In questa sezione viene illustrato come configurare l'app per lo sviluppo in realtà mista, ovvero aggiungendo una sessione AR. Per questa attività userai un asset di dati ARSessionConfig che include numerose impostazioni AR utili come il mapping spaziale e l'occlusione. Se vuoi approfondire questo argomento, la documentazione di Unreal Engine contiene altri dettagli sull'asset [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e sulla classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).

## <a name="objectives"></a>Obiettivi
* Uso delle impostazioni AR di Unreal Engine 
* Uso di un asset di dati ARSessionConfig
* Configurazione di un pedone e modalità di gioco

## <a name="adding-the-session-asset"></a>Aggiunta dell'asset della sessione
Le sessioni AR in Unreal non funzionano da sole. Per usare una sessione, è necessario un asset di dati ARSessionConfig con cui interagire, che costituisce la tua prossima attività:

1. Fai clic su **Add New > Miscellaneous > Data Asset** (Aggiungi nuovo > Varie > Asset dati) in **Content Browser** (Browser contenuto). Assicurati di essere nella cartella **Content** radice. 
    * Seleziona **ARSessionConfig**, fai clic su **Select** (Seleziona) e assegna all'asset il nome **ARSessionConfig**.

![Creazione di un'origine dati](images/unreal-uxt/3-createasset.PNG)

3. Fai doppio clic su **ARSessionConfig** per aprirlo, lascia tutte le impostazioni predefinite e premi **Save** (Salva). Torna alla finestra principale. 

![ARSessionConfig](images/unreal-uxt/3-arsessionconfig.PNG)

Al termine, il passaggio successivo consiste nell'assicurarsi che la sessione AR venga avviata quando viene caricato il livello e si arresti alla fine del livello. In Unreal è disponibile un particolare tipo di progetto denominato **Level Blueprint** (Progetto livello) che svolge la funzione di grafico eventi globale che prende come riferimento il livello. La connessione dell'asset ARSessionConfig in **Level Blueprint** (Progetto livello) garantisce l'avvio della sessione nel momento in cui viene avviato il gioco.

1. Fai clic su **Blueprints > Open Level Blueprint** (Progetti > Apri progetto livello) sulla barra degli strumenti dell'editor: 

![Open Level Blueprint (Apri progetto livello)](images/unreal-uxt/3-level-blueprint.PNG)

5. Trascina il nodo di esecuzione (freccia rivolta verso sinistra) fuori da **Event BeginPlay** (Evento BeginPlay) e rilascia. Cerca il nodo **Start AR Session** (Avvia sessione AR) e premi INVIO.  
    * Fai clic sull'elenco a discesa **Select Asset** (Seleziona asset) in **Session Config** (Configurazione sessione) e scegli l'asset **ARSessionConfig**. 

![Start AR Session (Avvia sessione AR)](images/unreal-uxt/3-start-ar-session.PNG)

6. Fai clic con il pulsante destro del mouse in un punto qualsiasi di EventGraph e crea un nuovo nodo **Event EndPlay**. Trascina e rilascia il pin di esecuzione. Cerca un nodo **Stop AR Session** (Arresta sessione AR) e premi INVIO. Se la sessione AR non viene arrestata al termine del livello, alcune funzionalità potrebbero smettere di funzionare se l'app viene riavviata durante lo streaming a un visore VR. 
    * Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale.

![Stop AR Session (Arresta sessione AR)](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Creare un pedone
A questo punto, il progetto necessita ancora di un oggetto Player. In Unreal, l'oggetto **Pawn** (Pedone) rappresenta l'utente del gioco, ma in questo caso sarà l'esperienza HoloLens 2.

1. Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** ed espandi la sezione **All Classes** (Tutte le classi) in fondo. 
    * Cerca **DefaultPawn**, fai clic su **Select** (Seleziona) e fai doppio clic sull'asset per aprirlo. 

![Creare un nuovo pedone basato su DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> Per impostazione predefinita, i pedoni hanno componenti mesh e collisione. Nella maggior parte dei progetti Unreal, i pedoni sono oggetti solidi che possono collidere con altri componenti. Dato che il pedone e l'utente coincidono nella realtà mista, è necessario poter passare attraverso gli ologrammi senza collisioni. 

2. Seleziona **CollisionComponent** nel pannello **Components** (Componenti) e scorri fino alla sezione **Collision** (Collisione) del pannello **Details** (Dettagli). 
    * Fai clic sull'elenco a discesa **Collision Presets** (Set di impostazioni di collisione) e cambia il valore in **NoCollision**. 
    * Esegui la stessa operazione per **MeshComponent** e fai clic su **Compile** (Compila) e **Save** (Salva) per salvare il progetto. 

![Modifica dei set di impostazioni di collisione del pedone](images/unreal-uxt/3-nocollision.PNG)

Al termine, torna alla finestra principale.

## <a name="create-a-game-mode"></a>Crea una modalità di gioco
Per completare la configurazione della realtà mista manca solo la modalità di gioco. La modalità di gioco determina una serie di impostazioni relative al gioco o all'esperienza, incluso il pedone predefinito da usare.

1.  Fai clic su **Add New > Blueprint Class** (Aggiungi nuovo > Classe progetto) nella cartella **Content** (Contenuto) ed espandi la sezione **All Classes** (Tutte le classi) in fondo. 
    * Cerca **Game Mode Base** (Base modalità gioco), assegna il nome **MRGameMode** e fai doppio clic per aprire l'elemento. 

![MRGameMode nel browser dei contenuti](images/unreal-uxt/3-gamemode.PNG)

2.  Passa alla sezione **Classes** (Classi) nel pannello **Details** (Dettagli) e modifica **Default Pawn Class** (Classe pedone predefinito) in **MRPawn**. 
    * Seleziona **Compile** (Compila) e **Save** (Salva) e torna alla finestra principale. 

![Impostazione della classe di pedone predefinita](images/unreal-uxt/3-setpawn.PNG)

3.  Seleziona **Edit > Projects Settings** (Modifica > Impostazioni progetti) e fai clic su **Maps & Modes** (Mappe e modalità) nell'elenco a sinistra. 
    * Espandi **Default Modes** (Modalità predefinite) e cambia **Default Game Mode** (Modalità gioco predefinita) in **MRGameMode**. 
    * Espandi **Default Maps** (Mappe predefinite) e imposta sia **EditorStartupMap** sia **GameDefaultMap** su **Main** (Principale). In questo modo, quando si chiude e si riapre l'editor o si usa il gioco, per impostazione predefinita viene selezionata la mappa principale.

![Project Settings - Maps & Modes (Impostazioni progetto - Mappe e modalità)](images/unreal-uxt/3-mapsandmodes.PNG)

Dopo avere completato la configurazione del progetto per la realtà mista, puoi passare all'esercitazione successiva e iniziare ad aggiungere input utente alla scena. 

[Sezione successiva: 4. Rendere la scena interattiva](unreal-uxt-ch4.md)