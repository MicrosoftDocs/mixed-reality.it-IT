---
title: 4. Rendere la scena interattiva
description: Parte 4 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: 2e4d26ed4e0b8199bfc629016aea688bd1c41ef8
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/18/2020
ms.locfileid: "83520026"
---
# <a name="4-making-your-scene-interactive"></a>4. Rendere la scena interattiva

Questa sezione presenta il plug-in open source UX Tools di Mixed Reality Toolkit, che fornisce un set di strumenti per rendere la scena interattiva. Al termine di questa sezione, i pezzi degli scacchi risponderanno all'input dell'utente. 

## <a name="objectives"></a>Obiettivi

* Includere il plug-in UX Tools di Mixed Reality Toolkit nel progetto
* Aggiungere attori di interazione manuale sulla punta delle dita
* Creare e collegare i manipolatori alla scacchiera e ai pezzi 
* Usare la simulazione dell'input per convalidare il progetto

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Scaricare il plug-in UX Tools di Mixed Reality Toolkit

1.  Clona o scarica e decomprimi la versione più recente del plug-in UX Tools di MRTK dal [repository GitHub UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases).

2.  Nella cartella radice del progetto degli scacchi crea una nuova cartella denominata "Plugins" (Plug-in). Copia il plug-in UX Tools decompresso in questa cartella. Riavvia l'editor di Unreal. 

![Creare una cartella dei plug-in del progetto](images/unreal-uxt/4-plugins.PNG)

3.  Dopo il riavvio, se il contenuto del plug-in UX Tools non viene visualizzato nel pannello delle origini, può essere necessario fare clic su **View Options > Show Plugin Content** (Opzioni di visualizzazione > Mostra contenuto plug-in). Noterai che il plug-in UX Tools fornisce una cartella Content (Contenuto) con le sottocartelle Pointers (Puntatori), Input Simulation (Simulazione di input) e Simple Button (Pulsante semplice), oltre a una cartella C++ Classes (Classi C++) con sottocartelle separate in base alla funzione.  

![Mostra contenuto plug-in](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>Generare attori di interazione manuale

1.  Iniziamo con la generazione di attori di interazione manuale dall'oggetto MRPawn in modo da 1) visualizzare MRPawn con un cursore sulla punta del dito indice del pedone 2) specificare eventi di input manuale articolati (e, di conseguenza, manipolare direttamente gli attori) tramite il pedone e 3) specificare eventi di input di interazione da lontano tramite raggi che si estendono dal palmo della mano. Apri il progetto **MRPawn** e passa a **Event Graph** (Grafico evento). 

2.  Trascina il segnaposto di esecuzione da Event BeginPlay (Evento inizio partita) e rilascialo per inserire un nuovo nodo. Seleziona il nodo **Spawn Actor from Class** (Genera attore dalla classe). Fai clic sull'elenco a discesa accanto al segnaposto **Class** (Classe) e cerca **Uxt Hand Interaction Actor** (Attore di interazione manuale Uxt). Trascina il segnaposto di esecuzione dal nodo SpawnActor Uxt Hand Interaction (Genera attore - Interazione manuale Uxt), rilascia e cerca la funzione **Set Hand** (Imposta mano) contenuta nella classe Uxt Hand Interaction Actor (Attore di interazione manuale Uxt). Connetti il valore restituito del nodo SpawnActor (Genera attore) al segnaposto di destinazione del nodo Set Hand (Imposta mano) per impostare la mano dell'attore di interazione manuale su **Left** (Sinistra). Genera un secondo **attore di interazione manuale Uxt**, questa volta impostando la mano su **Right** (Destra), in modo che, quando l'evento viene avviato, viene generato un attore di interazione manuale Uxt su ogni mano. 

![Generare attori di interazione manuale Uxt](images/unreal-uxt/4-spawnactor.PNG)

3.  A questo punto, dobbiamo fornire agli attori di interazione manuale Uxt una trasformazione iniziale in cui generare e un proprietario. Trascina il segnaposto fuori da uno dei segnaposto **Spawn Transform** (Genera trasformazione) e rilascia per inserire un nuovo nodo. Cerca il nodo **Make Transform** (Crea trasformazione). La trasformazione iniziale in realtà non è importante perché gli attori di interazione manuale passano da una mano all'altra non appena sono visibili (codice scritto automaticamente nel plug-in UX Tools). In caso contrario, scompariranno. La funzione SpawnActor (Genera attore) richiede, tuttavia, una trasformazione come input, per evitare un errore del compilatore. Manterremo quindi i valori predefiniti in Make Transform (Crea trasformazione) così come sono. Trascina il **valore restituito** di Make Transform (Crea trasformazione) anche su Interaction Actor Spawn Transform (Attore di interazione - Genera trasformazione) dell'altra mano. 

4.  Fai clic sulla **freccia verso il basso** nella parte inferiore di entrambi i nodi SpawnActor (Genera attore) per visualizzare il segnaposto **Owner** (Proprietario). Trascina il segnaposto fuori da uno dei segnaposto **Owner** (Proprietario) e rilascialo per inserire un nuovo nodo. Cerca "self" e seleziona la variabile **Get a reference to self** (Ottieni riferimento a Self). Crea un collegamento tra il nodo di riferimento all'oggetto Self e l'altro segnaposto Owner (Proprietario) dell'attore di interazione manuale. Trascina i nodi per rendere il progetto più leggibile. **Compila**, **Salva** e torna alla finestra principale. 

![Configurazione completa dell'attore di interazione manuale Uxt](images/unreal-uxt/4-fingerptrs.PNG)

Per altre informazioni sull'attore di interazione manuale specificato nel plug-in UX Tools di MRTK, consulta la [documentazione ufficiale](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).

## <a name="attach-manipulators"></a>Collegare i manipolatori

1.  Successivamente, collegheremo i manipolatori alla scacchiera e agli attori Re. Un manipolatore è un componente che risponde a input della mano articolati e può essere afferrato, ruotato e spostato. Applicando la trasformazione del manipolatore a quella di un attore, gli attori possono essere manipolati direttamente. 

2.  Apri il progetto Board (Tavola). Nel pannello **Components** (Componenti) fai clic su **Add Component** (Aggiungi componente) e cerca **Uxt Generic Manipolator** (Manipolatore generico Uxt). Nel pannello Details (Dettagli) è disponibile una sezione intitolata **Generic Manipulator** (Manipolatore generico) in cui puoi specificare se vuoi abilitare una manipolazione con una o due mani, la modalità di rotazione e lo smussamento. Seleziona la modalità desiderata e quindi **Compile** (Compila) e **Save** (Salva) la tavola. 

![Aggiungere un manipolatore generico](images/unreal-uxt/4-addmanip.PNG)

![Impostare la modalità](images/unreal-uxt/4-setrotmode.PNG)

3.  Ripeti i passaggi precedenti per l'attore WhiteKing.

Per altre informazioni sui componenti del manipolatore disponibili nel plug-in UX Tools di MRTK, consulta la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html) ufficiale.

## <a name="test-out-your-scene-with-simulated-hands"></a>Testare la scena con le mani simulate

1.  Nella finestra principale premere **Play**. Visualizzerai due mani con mesh fornite dal plug-in UX Tools di MRTK, con i raggi della mano che si estendono dal palmo. 

![Mani simulate nel riquadro di visualizzazione](images/unreal-uxt/4-handsim.PNG)

2.  Per controllare la **mano destra**, tieni premuto il pulsante **ALT** sinistro. Per muovere la mano, sposta il mouse. Per spostare la mano **avanti** o **indietro**, scorri con la **rotellina del mouse**. Fai clic sul pulsante sinistro del mouse per **pizzicare** e sul pulsante centrale del mouse per **picchiettare con le dita**.

3.  Per controllare la **mano sinistra**, tieni premuto il pulsante **MAIUSC** sinistro. I controlli per spostare la mano sinistra sono uguali a quelli per la mano destra. 

4.  A questo punto, prova a usare le mani simulate per sollevare, spostare e appoggiare il re bianco degli scacchi. Puoi manipolare anche la tavola. Prova a usare l'interazione da vicino e da lontano. Tieni presente che, quando le mani si avvicinano abbastanza da poter afferrare direttamente la tavola e il re, il raggio della mano scompare e viene sostituito con un cursore a forma di dito sulla punta dell'indice. 

Per altre informazioni sulla funzionalità delle mani simulate fornita dal plug-in UX Tools di MRTK, consulta la [documentazione](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html) ufficiale.

[Sezione successiva: 5. Aggiunta di un pulsante e reimpostazione delle posizioni della parte](unreal-uxt-ch5.md)
