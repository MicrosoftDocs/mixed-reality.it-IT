---
title: Uso di Vuforia con Unity
description: Sfrutta Vuforia per creare applicazioni di realtà miste Windows in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcatori, coordinate, frame di riferimento, rilevamento
ms.openlocfilehash: bae5d0eb04ab9434dd3e72674686743779a8f70c
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003190"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motore Vuforia con Unity

Il motore Vuforia offre una funzionalità importante per HoloLens: la potenza di connettere le esperienze AR a immagini e oggetti specifici nell'ambiente. È possibile usare questa funzionalità per sovrapporre istruzioni dettagliate guidate sui macchinari per l'azienda industriale o aggiungere funzionalità e esperienze digitali a un prodotto o gioco fisico.

Per una maggiore flessibilità nello sviluppo di esperienze AR, il motore Vuforia offre un'ampia gamma di funzionalità e destinazioni. Una delle funzionalità più recenti, Vuforia Model targets, è una funzionalità chiave per usi sia commerciali che industriali. Le destinazioni dei modelli consentono alle applicazioni di riconoscere oggetti fisici, ad esempio computer, automobili o giocattoli, e di tenerne traccia in base a un modello CAD o digitale 3D. Per gli usi industriali, questa funzionalità può fornire agli addetti agli assembly e ai tecnici del servizio le istruzioni di lavoro AR e le linee guida procedurali in fabbrica o nel campo.

Le app esistenti del motore Vuforia compilate per telefoni e tablet possono essere facilmente configurate in Unity per l'esecuzione in HoloLens. È anche possibile usare il motore Vuforia per portare la nuova app HoloLens a Tablet Windows 10, ad esempio Surface Pro e Surface book.


## <a name="get-the-tools"></a>Scarica gli strumenti

[Installare le versioni consigliate](install-the-tools.md) di Visual Studio e Unity, quindi configurare Unity per l'uso di Visual Studio e dell'IDE e del compilatore preferiti. 

Quando si installa Unity, assicurarsi di installare il "back-end di scripting di Windows Store IL2CPP".

L'aggiunta del supporto del motore Vuforia funziona in modo diverso a seconda della versione di Unity:
*   Unity 2018,4: scaricare il programma di installazione del motore Vuforia per Unity 2018,4 dal portale per sviluppatori Vuforia
*   Unity 2019,2: ottenere il [pacchetto del motore Vuforia](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html) più recente 

## <a name="getting-started-with-vuforia-engine"></a>Introduzione al motore Vuforia

Il punto di partenza migliore per imparare a usare il motore Vuforia con HoloLens è con l' [esempio HoloLens Engine Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) , disponibile in Unity Store di Unity. L'esempio fornisce un progetto HoloLens completo che include scene preconfigurate che possono essere distribuite in un HoloLens.

Le scene illustrano come usare le destinazioni delle immagini Vuforia per riconoscere un'immagine e aumentarla con contenuto digitale in un'esperienza HoloLens. L'esempio Hololens del motore Vuforia include anche una scena che mostra l'utilizzo delle destinazioni dei modelli e di VuMarks in HoloLens. È possibile sostituire facilmente il proprio contenuto nelle scene per sperimentare la creazione di app HoloLens che usano il motore Vuforia.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurazione di un'app Vuforia per HoloLens

Lo sviluppo di un'app del motore Vuforia per HoloLens è fondamentalmente lo stesso dello sviluppo di app del motore Vuforia per altri dispositivi. È quindi possibile applicare le impostazioni e le configurazioni di compilazione descritte nella sezione seguente. Questo è tutto ciò che serve per consentire al motore Vuforia di funzionare con il mapping spaziale HoloLens e i sistemi di rilevamento posizionale.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilare ed eseguire l'esempio di motore Vuforia per HoloLens
1.  Scaricare l' [esempio di motore Vuforia per HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) da Unity Asset Store
2.  Applicare le [Opzioni consigliate del motore Unity per l'alimentazione e le prestazioni](performance-recommendations-for-unity.md)
3.  Aggiungere le scene di esempio alle scene nella compilazione.
4.  Impostare la destinazione di compilazione della piattaforma per "piattaforma UWP (Universal Windows Platform)" nelle impostazioni di compilazione file >.
5.  Selezionare le seguenti impostazioni di configurazione della piattaforma di compilazione: 
   * Dispositivo di destinazione = HoloLens
   * Tipo di compilazione = D3D
   * SDK = Ultima versione installata
   * Visual Studio Version = versione più recente installata
   * Compilazione ed esecuzione in = computer locale
6.  Definire un **nome di prodotto**univoco, in **Impostazioni lettore**, per fungere da nome dell'app quando viene installato in HoloLens.
7.  Controllare la **realtà aumentata di Vuforia** e la **realtà virtuale supportata** nelle impostazioni del **lettore > le impostazioni di XR**
8.  Inoltre, in **Impostazioni XR**, assicurarsi che "realtà mista di Windows" venga aggiunto all'elenco di **SDK di realtà virtuale**
9.  Controllare le funzionalità seguenti nelle impostazioni del lettore > impostazioni di pubblicazione 
   * InternetClient
   * WebCam
   * SpatialPerception-se si intende usare l'API Observer di Surface
10. Selezionare Compila per generare un progetto di Visual Studio
11. Compilare il file eseguibile da Visual Studio e installarlo nella HoloLens

Nota: a partire dalla versione 7,2, l'esempio di motore Vuforia per HoloLens include una scena di esempio che include l'uso di esempio delle destinazioni dei modelli

## <a name="the-vuforia-developer-portal"></a>Portale per sviluppatori Vuforia

Gli sviluppatori che desiderano creare le proprie esperienze AR con il motore Vuforia e HoloLens devono iscriversi nel portale per sviluppatori Vuforia in [Developer.Vuforia.com](https://developer.vuforia.com/). Nel portale gli sviluppatori hanno accesso ai forum del [motore Vuforia](https://developer.vuforia.com/forum) , in cui possono partecipare a discussioni della community, una [libreria](https://library.vuforia.com/) con una documentazione dettagliata su tutte le funzionalità del motore Vuforia e la [gestione di destinazione Vuforia](https://developer.vuforia.com/target-manager) in cui gli utenti possono creare le proprie destinazioni personalizzate. Gli sviluppatori possono inoltre iscriversi per ottenere una licenza gratuita per sviluppatori utilizzando il [gestore delle licenze Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Rilevamento esteso con Vuforia

Il [rilevamento esteso](https://library.vuforia.com/articles/Training/Extended-Tracking) mantiene il rilevamento anche quando una destinazione non è più in visualizzazione. Viene abilitata automaticamente per tutte le destinazioni quando è abilitato il rilevamento del dispositivo posizionale. Per le applicazioni HoloLens, lo strumento di rilevamento del dispositivo posizionale viene avviato automaticamente in Unity.

Il motore Vuforia unisce automaticamente le pose dal rilevamento della fotocamera e dal rilevamento spaziale di HoloLens per fornire una destinazione stabile, indipendentemente dal fatto che la destinazione sia visibile o meno dalla fotocamera.

Poiché il processo viene gestito automaticamente, non richiede alcuna programmazione da parte dello sviluppatore.


**Ecco cosa accade...**
1. Il Tracker di destinazione di Vuforia riconosce la destinazione
2. Il rilevamento della destinazione viene quindi inizializzato
3. La posizione e la rotazione della destinazione vengono analizzate per fornire una stima di posa affidabile per HoloLens
4. Il motore Vuforia trasforma il posto della destinazione nello spazio delle coordinate del mapping spaziale HoloLens
5. HoloLens acquisisce il controllo se la destinazione non è più in visualizzazione. Ogni volta che si cerca di nuovo nella destinazione, Vuforia continuerà a tenere traccia delle immagini e degli oggetti in modo accurato.

Le destinazioni rilevate, ma non più visualizzate, vengono segnalate come EXTENDED_TRACKED. In questi casi, lo script DefaultTrackableEventHandler usato in tutte le destinazioni continua a eseguire il rendering del contenuto di aumento. Lo sviluppatore può controllare questo comportamento implementando uno script personalizzato del gestore eventi rilevabili.


## <a name="performance-mode-with-vuforia-engine"></a>Modalità prestazioni con il motore Vuforia 

È possibile usare il motore Vuforia per gestire le prestazioni in HoloLens per l'estensione delle esperienze AR e ridurre il carico di lavoro sulla CPU. Il motore Vuforia offre tre modalità che è possibile selezionare: predefinita, per ottimizzare la velocità e ottimizzare la qualità. 

*   MODE_OPTIMIZE_SPEED consente di ridurre al minimo il carico di lavoro nel dispositivo HoloLens ed è ideale per estendere le esperienze AR. È consigliabile per le situazioni in cui l'app tiene traccia degli oggetti/destinazioni statici.
*   MODE_DEFAULT è la modalità normale che può essere usata nella maggior parte degli scenari.
*   MODE_OPTIMIZE_QUALITY è migliore per tenere traccia degli obiettivi mobili o degli obiettivi del modello che si prevede di prelevare.

**Impostazione della modalità**

Per modificare la modalità di prestazioni in Unity, passare a configurazione di Vuforia (CTRL + MAIUSC + V/Cmd + Maiusc + V) che si trova come componente in ARCamera GameObject. 
*   Selezionare il menu a discesa per la modalità dispositivo fotocamera e selezionare una delle tre opzioni.


## <a name="see-also"></a>Vedi anche
* [Installare gli strumenti](install-the-tools.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale](spatial-mapping.md)
* [Fotocamera in Unity](camera-in-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentazione di Vuforia: sviluppo per Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentazione di Vuforia: come installare l'estensione di Unity Vuforia](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentazione di Vuforia: uso dell'esempio HoloLens in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentazione di Vuforia: rilevamento esteso in Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
