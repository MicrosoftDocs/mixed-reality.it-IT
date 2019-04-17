---
title: Uso di Vuforia con Unity
description: Sfruttare Vuforia per compilare applicazioni di realtà mista di Windows in Unity.
author: ChimeraScorn
ms.author: cwhite
ms.date: 03/21/2018
ms.topic: article
keywords: Vuforia, marcatori, coordinate, frame di riferimento, di rilevamento
ms.openlocfilehash: 43a74989b931fee898af0aeae9e240303b2eef01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603172"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motore Vuforia con Unity

Vuforia motore offre una funzionalità importante per HoloLens: power per la connessione AR esperienze immagini specifiche e oggetti nell'ambiente. È possibile usare questa funzionalità per sovrapporre guidate istruzioni dettagliate su macchine per le aziende industriali o aggiungere esperienze e funzionalità digitali a un prodotto fisico o del tuo gioco. 

Per una maggiore flessibilità durante lo sviluppo di AR esperienze, motore Vuforia offre un'ampia gamma di funzionalità e destinazioni. Una delle funzionalità più recenti, Vuforia modello destinazioni, è una funzionalità chiave per usi commerciali e industriale. Modello destinazioni consentono alle applicazioni riconoscere gli oggetti fisici come macchine, automobili o toys e tenerne traccia basata su una CAD o un modello 3D digitale. Per utilizzi industriali, questa funzionalità può fornire i ruoli di lavoro di assembly e i tecnici del servizio con AR out nel campo o usare le istruzioni e linee guida procedura mentre nell'ambiente di produzione. 

App Vuforia Engine esistenti che sono state compilate per telefoni e Tablet possono essere configurate con facilità in Unity per l'esecuzione su HoloLens. Vuforia motore si permette anche di sfruttare la nuova app per HoloLens per Tablet Windows 10, ad esempio il 4 Surface Pro e un Surface Book.

## <a name="get-the-tools"></a>Scarica gli strumenti

[Installare le versioni consigliate](install-the-tools.md) di Visual Studio e Unity, quindi configurare Unity per l'uso di Visual Studio e l'IDE e compilatore preferito. 

Durante l'installazione di Unity, assicurarsi di installare "Windows Store .NET Scripting back-end" o "Windows Store IL2CPP Scripting back-end". Inoltre, assicurarsi di selezionare "Vuforia ampliata realtà" supporto per abilitare un motore Vuforia di Unity.


## <a name="getting-started-with-vuforia-engine"></a>Guida introduttiva a Vuforia motore

Poiché Vuforia motore è integrato in Unity, gli sviluppatori non devono scaricare o installare strumenti aggiuntivi. La versione consigliata di Unity è il flusso LTS che corrisponde a 2017.3 e include il motore di Vuforia 7.0.57. Il miglior punto di partenza per la formazione sull'uso del motore Vuforia con HoloLens è con il [Vuforia motore HoloLens esempio](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponibile in Store l'Asset Unity). L'esempio fornisce un progetto di HoloLens completo incluso scene preconfigurate che possono essere distribuite in un HoloLens.

In background Mostra come usare le destinazioni di immagine Vuforia per riconoscere un'immagine e aggiungere contenuto digitale in un'esperienza di HoloLens. Gli sviluppatori che usano versioni più recenti di Unity e Vuforia hanno accesso a esempi aggiornati che includono una scena che illustra l'utilizzo del modello di destinazioni in HoloLens. È possibile sostituire facilmente il proprio contenuto in background per provare a usare la creazione di App di HoloLens che usa Vuforia motore.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Configurazione di un'App Vuforia per HoloLens

Sviluppo di un'app Vuforia Engine per HoloLens è fondamentalmente quello utilizzato per lo sviluppo di App Vuforia Engine per altri dispositivi. È quindi possibile applicare le impostazioni di compilazione e configurazioni descritte nella sezione seguente. Che è tutto ciò che serve per abilitare motore Vuforia per collaborare con il mapping spaziale HoloLens e posizionali sistemi di rilevamento.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilare ed eseguire l'esempio di motore Vuforia per HoloLens
1.  Scaricare il [esempio di motore Vuforia per HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) da Store di Asset di Unity
2.  Applicare il [consigliato opzioni del motore Unity per l'alimentazione e delle prestazioni](performance-recommendations-for-unity.md)
3.  Aggiungere le quinte di esempio per le scene nella compilazione.
4.  Impostare la piattaforma di destinazione di compilazione per "Universal Windows Platform" nel File > Build Settings.
5.  Selezionare le impostazioni di configurazione di compilazione della piattaforma seguenti: 
   * Dispositivo di destinazione = HoloLens
   * Tipo di compilazione = D3D
   * SDK più recente = installato
   * Versione di Visual Studio = versione più recente installata
   * Compilare ed eseguire = nel computer locale
6.  Definire un valore univoco **Product Name**, nel **le impostazioni del giocatore**, come il nome dell'app installato di HoloLens durante.
7.  Controllare **Vuforia ampliata realtà** e **realtà virtuale supportato** in **le impostazioni del giocatore > Impostazioni XR**
8.  Anche in **impostazioni XR**, assicurarsi che "Windows Mixed Reality" verrà aggiunto il **SDK di realtà virtuale** elenco
9.  Controllare le funzionalità seguenti nelle impostazioni di Windows Media Player > Impostazioni di pubblicazione 
   * InternetClient
   * WebCam
   * SpatialPerception - se si prevede di usare l'API di osservatore area
10. Selezionare compilazione per generare un progetto di Visual Studio
11. Compilare l'eseguibile da Visual Studio e installarlo di HoloLens

Nota: A partire dalla versione 7.2, l'esempio di motore Vuforia per HoloLens include una scena di esempio incluso l'utilizzo di esempio di modello destinazioni

## <a name="the-vuforia-developer-portal"></a>Il portale per sviluppatori Vuforia

Gli sviluppatori che vogliono per creare le proprie AR esperienze con il motore Vuforia e HoloLens consigliabile effettuare l'iscrizione nel portale per gli sviluppatori Vuforia alla [developer.vuforia.com](https://developer.vuforia.com/). Nel portale, gli sviluppatori hanno accesso alla [Vuforia motore forum](https://developer.vuforia.com/forum) dove è possibile partecipare alle discussioni della community, un [libreria](https://library.vuforia.com/) con documentazione dettagliata su tutte le funzionalità del motore Vuforia e il [ Gestione di destinazione Vuforia](https://developer.vuforia.com/target-manager) in cui gli utenti possono creare i propri destinazioni personalizzate. Gli sviluppatori possono anche iscriversi per una licenza per sviluppatori gratuito usando la [Vuforia License Manager](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Rilevamento esteso con Vuforia

[Rilevamento esteso](https://library.vuforia.com/articles/Training/Extended-Tracking) crea una mappa dell'ambiente per mantenere verifica anche quando una destinazione non è più visualizzata. È la controparte Vuforia motori per il mapping spaziale eseguita da HoloLens. Quando si abilita rilevamento esteso in una destinazione, si abilita la posa del server di destinazione che deve essere passato al sistema di mapping spaziale. In questo modo, le destinazioni possono esistere in sistemi di coordinate spaziali il motore Vuforia e HoloLens, ma non contemporaneamente.

![Finestra delle impostazioni di Unity](images/vuforia-extendedtracking.png)<br>
*Finestra delle impostazioni di Unity*

**Attivazione del rilevamento esteso su una destinazione**

Vuforia motore automaticamente trasformerà il posa di una destinazione che utilizza il rilevamento delle estesa al sistema di coordinate spaziale HoloLens. In questo modo HoloLens acquisire la proprietà di rilevamento e integrare qualsiasi contenuto in modo da integrare nella mappa spaziale dell'ambiente circostante della destinazione. Questo processo si verifica tra Vuforia motore e realtà mista API in Unity e non richiede alcuna attività di programmazione dello sviluppatore: viene gestita automaticamente.

**Ecco ciò che accade...**
1. Destinazione del Vuforia Tracker riconosce la destinazione
2. Destinazione di rilevamento viene quindi inizializzata
3. La posizione e la rotazione della destinazione vengano analizzate al fine di fornire una stima posa affidabile per HoloLens da usare
4. Vuforia trasforma lo spazio delle coordinate mapping spaziale HoloLens di posa della destinazione
5. HoloLens accetta rispetto al rilevamento e lo strumento di rilevamento Vuforia viene disattivato

Lo sviluppatore può controllare questo processo, per restituire il controllo alla Vuforia, disabilitando il monitoraggio esteso nel TargetBehaviour.

**NOTA:** A partire da Vuforia 7.2, esteso di rilevamento non è più abilitata in base a una per ogni destinazione. Al contrario, gli sviluppatori possono disattivare sul dispositivo di rilevamento per abilitare una funzionalità simile in tutte le destinazioni nella scena.


## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Mapping spaziale](spatial-mapping.md)
* [Fotocamera in Unity](camera-in-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio a Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia documentazione: Sviluppo per Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia documentazione: Come installare l'estensione Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia documentazione: Utilizzo con l'esempio di HoloLens in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia documentazione: Rilevamento esteso in Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
