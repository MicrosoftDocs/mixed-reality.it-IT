---
title: Uso di Vuforia con Unity
description: Sfrutta Vuforia per creare applicazioni di realtà miste Windows in Unity.
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcatori, coordinate, frame di riferimento, rilevamento
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750348"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motore Vuforia con Unity

Il motore Vuforia offre una funzionalità importante per HoloLens: la potenza di connettere le esperienze AR a immagini e oggetti specifici nell'ambiente. È possibile usare questa funzionalità per sovrapporre istruzioni dettagliate guidate sui macchinari per l'azienda industriale o aggiungere funzionalità e esperienze digitali a un prodotto o gioco fisico. 

Per una maggiore flessibilità nello sviluppo di esperienze AR, il motore Vuforia offre un'ampia gamma di funzionalità e destinazioni. Una delle funzionalità più recenti, Vuforia Model targets, è una funzionalità chiave per usi sia commerciali che industriali. Le destinazioni dei modelli consentono alle applicazioni di riconoscere oggetti fisici, ad esempio computer, automobili o giocattoli, e di tenerne traccia in base a un modello CAD o digitale 3D. Per gli usi industriali, questa funzionalità può fornire agli addetti agli assembly e ai tecnici del servizio le istruzioni di lavoro AR e le linee guida procedurali in fabbrica o nel campo. 

Le app esistenti del motore Vuforia compilate per telefoni e tablet possono essere facilmente configurate in Unity per l'esecuzione in HoloLens. È anche possibile usare il motore Vuforia per portare la nuova app HoloLens a Tablet Windows 10, ad esempio Surface Pro 4 e Surface book.

## <a name="get-the-tools"></a>Scarica gli strumenti

[Installare le versioni consigliate](install-the-tools.md) di Visual Studio e Unity, quindi configurare Unity per l'uso di Visual Studio e dell'IDE e del compilatore preferiti. 

Quando si installa Unity, assicurarsi di installare "Windows Store .NET Scripting backend" o "Windows Store IL2CPP scripting backend". Assicurarsi anche di selezionare "supporto per la realtà aumentata Vuforia" per abilitare il motore Vuforia in Unity.


## <a name="getting-started-with-vuforia-engine"></a>Introduzione al motore Vuforia

Poiché il motore Vuforia è integrato in Unity, gli sviluppatori non devono scaricare o installare strumenti aggiuntivi. La versione consigliata di Unity è il flusso LTS attualmente in 2017,3 e include il motore Vuforia 7.0.57. Il punto di partenza migliore per imparare a usare il motore Vuforia con HoloLens è con l' [esempio HoloLens Engine Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) , disponibile in Unity Store di Unity. L'esempio fornisce un progetto HoloLens completo che include scene preconfigurate che possono essere distribuite in un HoloLens.

Le scene illustrano come usare le destinazioni delle immagini Vuforia per riconoscere un'immagine e aumentarla con contenuto digitale in un'esperienza HoloLens. Gli sviluppatori che usano versioni più recenti di Unity e Vuforia hanno accesso agli esempi aggiornati che includono una scena che mostra l'uso delle destinazioni dei modelli in HoloLens. È possibile sostituire facilmente il proprio contenuto nelle scene per sperimentare la creazione di app HoloLens che usano il motore Vuforia.


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

Nota: A partire dalla versione 7,2, l'esempio di motore Vuforia per HoloLens include una scena di esempio, incluso l'utilizzo di esempio delle destinazioni dei modelli

## <a name="the-vuforia-developer-portal"></a>Portale per sviluppatori Vuforia

Gli sviluppatori che desiderano creare le proprie esperienze AR con il motore Vuforia e HoloLens devono iscriversi nel portale per sviluppatori Vuforia in [Developer.Vuforia.com](https://developer.vuforia.com/). Nel portale gli sviluppatori hanno accesso ai forum del [motore Vuforia](https://developer.vuforia.com/forum) in cui possono partecipare a discussioni della community, una [libreria](https://library.vuforia.com/) con una documentazione dettagliata su tutte le funzionalità del motore Vuforia e la [gestione di destinazione Vuforia](https://developer.vuforia.com/target-manager) in cui gli utenti possono creare destinazioni personalizzate. Gli sviluppatori possono inoltre iscriversi per ottenere una licenza gratuita per sviluppatori utilizzando il [gestore delle licenze Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Rilevamento esteso con Vuforia

Il [rilevamento esteso](https://library.vuforia.com/articles/Training/Extended-Tracking) crea una mappa dell'ambiente per mantenere il rilevamento anche quando una destinazione non è più in visualizzazione. Si tratta di una controparte dei motori Vuforia per il mapping spaziale eseguito da HoloLens. Quando si Abilita il rilevamento esteso in una destinazione, si Abilita la definizione della destinazione per il sistema di mapping spaziale. In questo modo, le destinazioni possono esistere sia nel motore Vuforia che nei sistemi di coordinate spaziali HoloLens, anche se non contemporaneamente.

![Finestra impostazioni di Unity](images/vuforia-extendedtracking.png)<br>
*Finestra impostazioni di Unity*

**Abilitazione del rilevamento esteso in una destinazione**

Il motore Vuforia trasformerà automaticamente la definizione di una destinazione che utilizza il rilevamento esteso nel sistema di coordinate spaziali HoloLens. Ciò consente a HoloLens di eseguire il monitoraggio e di integrare eventuali contenuti che si ampliano nella mappa spaziale degli ambienti di destinazione. Questo processo si verifica tra il motore Vuforia e le API di realtà mista in Unity e non richiede alcuna programmazione da parte dello sviluppatore, ma viene gestito automaticamente.

**Ecco cosa accade...**
1. Il Tracker di destinazione di Vuforia riconosce la destinazione
2. Il rilevamento della destinazione viene quindi inizializzato
3. La posizione e la rotazione della destinazione vengono analizzate per fornire una stima di posa affidabile per l'uso da parte di HoloLens
4. Vuforia trasforma il posto della destinazione nello spazio delle coordinate del mapping spaziale HoloLens
5. HoloLens acquisisce il controllo e il Vuforia Tracker è disattivato

Lo sviluppatore può controllare questo processo, per restituire il controllo a Vuforia, disabilitando il rilevamento esteso in TargetBehaviour.

**NOTA:** A partire da Vuforia 7,2, il rilevamento esteso non è più abilitato per ogni singola destinazione. Gli sviluppatori possono invece attivare il rilevamento dei dispositivi per abilitare funzionalità simili in tutte le destinazioni della scena.


## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale](spatial-mapping.md)
* [Fotocamera in Unity](camera-in-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentazione di Vuforia: Sviluppo per Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentazione di Vuforia: Come installare l'estensione Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentazione di Vuforia: Uso dell'esempio HoloLens in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentazione di Vuforia: Rilevamento esteso in Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
