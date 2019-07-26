---
title: Test dell'app in HoloLens
description: Linee guida e suggerimenti per il test dell'app HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, test
ms.openlocfilehash: b8c8e7ea8f90633cbb3b2aa01764398ef9a5c12a
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507903"
---
# <a name="testing-your-app-on-hololens"></a>Test dell'app in HoloLens

Il test delle applicazioni HoloLens è molto simile a quello delle applicazioni Windows. Tutte le aree comuni devono essere considerate (funzionalità, interoperabilità, prestazioni, sicurezza, affidabilità e così via). Esistono, tuttavia, alcune aree che richiedono una particolare gestione o attenzione ai dettagli che non vengono in genere osservati nelle app per PC o telefoni. Le app olografiche devono essere eseguite senza problemi in un set eterogeneo di ambienti. Devono inoltre mantenere sempre le prestazioni e la comodità degli utenti. Le linee guida per il test di queste aree sono descritte in dettaglio in questo argomento.

## <a name="performance"></a>Prestazioni

Le app olografiche devono essere eseguite senza problemi in un set eterogeneo di ambienti. Devono inoltre mantenere sempre le prestazioni e la comodità degli utenti. Le prestazioni sono molto importanti per l'esperienza dell'utente con un'app olografica a cui è dedicato un intero argomento. Assicurarsi di leggere e seguire le [prestazioni di comprensione per la realtà mista](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Test 3D in 3D
1. **Testare l'app in tutti gli spazi diversi possibili.** Prova in grandi sale, piccoli spazi, bagni, cucine, camere, uffici e così via. Prendere in considerazione anche le camere con funzionalità non standard, ad esempio muri non verticali, muri curvi, massimali non orizzontali. Funziona bene durante la transizione tra chat room, piani, attraversamento di corridoi o scale?
2. **Testare l'app in condizioni di illuminazione diverse.** Risponde correttamente a condizioni ambientali diverse, ad esempio illuminazione, superfici nere, superfici trasparenti o riflettenti, ad esempio specchi, pareti vetrate e così via.
3. **Testare l'app in condizioni di movimento diverse.** Inserire sul dispositivo e provare gli scenari in diversi Stati di movimento. Risponde correttamente a uno stato di spostamento o costante diverso?
4. **Testare il funzionamento dell'app da diverse angolazioni.** Se si dispone di un ologramma bloccato in tutto il mondo, cosa accade se l'utente si aggira? Cosa accade se si verifica qualcosa tra l'utente e l'ologramma? Cosa accade se l'utente esamina l'ologramma sopra o sotto?
5. **Usare i segnali spaziali e audio.** Assicurarsi che l'app li usi per impedire che l'utente vada perso.
6. **Testare l'app a diversi livelli di rumore di ambiente.** Se sono stati implementati i comandi vocali, provare a richiamarli con diversi livelli di rumore di ambiente.
7. **Testare l'app in sede e in piedi**. Assicurarsi di eseguire il test dalle posizioni di seduta e di posizione.
8. **Testare l'app da diverse distanze**. Gli elementi dell'interfaccia utente possono essere letti e interagire da lontano? L'app reagirà agli utenti troppo vicini agli ologrammi?
9. **Testare l'app in base alle interazioni comuni della barra delle app**. Tutti i riquadri delle app e le app universali 2D hanno una [barra dell'app](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) che consente di controllare il modo in cui l'app viene posizionata nel mondo misto. Assicurarsi che facendo clic su Rimuovi si interrompa normalmente il processo dell'app e che il pulsante indietro sia supportato nel contesto dell'app universale 2D. Provare a ridimensionare e spostare l'app in [modalità di regolazione](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) sia quando è attiva, sia quando si tratta di un riquadro dell'app sospesa.

### <a name="environmental-test-matrix"></a>Matrice di test ambientali

![Matrice di test dell'ambiente per lo sviluppo di app HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comfort
1. **Ritagliare i piani.** Prestare attenzione alla posizione in cui [viene eseguito il rendering](hologram-stability.md#hologram-render-distances)degli ologrammi.
2. **Evitare lo spostamento virtuale incoerente con lo spostamento Head effettivo.** Evitare lo spostamento della fotocamera in modo che non sia rappresentativo del movimento effettivo dell'utente. Se l'app richiede lo spostamento dell'utente tramite una scena, rendere prevedibile il movimento, ridurre al minimo l'accelerazione e consentire all'utente di controllare il movimento.
3. **Seguire le linee guida per la qualità degli ologrammi.** Le app performanti che implementano le [linee guida](hologram-stability.md) relative alla qualità olografica hanno una minore probabilità di causare disagio nell'utente.
4. **Distribuisci gli ologrammi orizzontalmente anziché verticalmente.** Forzare l'utente a dedicare lunghi periodi di tempo alla ricerca verso l'alto o verso il basso può causare fatica nel collo.

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>Sguardi e movimenti

[Sguardi](gaze.md) è una forma di base di input in HoloLens che consente agli utenti di puntare agli ologrammi e all'ambiente. È possibile visualizzare visivamente la destinazione dello sguardo in base alla posizione del cursore. È normale associare il cursore a sguardi con un cursore del mouse.

I [movimenti](gestures.md) sono la modalità di interazione con gli ologrammi, ad esempio un clic del mouse. Nella maggior parte dei casi, i comportamenti del mouse e del tocco sono gli stessi, ma è importante comprendere e convalidare quando si differenziano.

**Verificare quando l'app ha un comportamento diverso con il mouse e il tocco.** In questo modo si identificano le incoerenze e si aiutano a prendere decisioni di progettazione per rendere più naturale l'esperienza per gli utenti. Ad esempio, l'attivazione di un'azione in base al passaggio del mouse.

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.

### <a name="custom-voice-commands"></a>Comandi vocali personalizzati

L' [input vocale](voice-input.md) è una forma naturale di interazione. L'esperienza utente può essere magica o confusa a seconda dei comandi scelti e del modo in cui vengono esposti. Di norma, non usare i comandi vocali di sistema, ad esempio "Select" o "Hey Cortana" come comandi personalizzati. Di seguito sono riportati alcuni punti da considerare:
1. **Evitare l'uso di comandi che hanno un suono simile.** Questo può potenzialmente attivare il comando errato.
2. **Quando possibile, scegliere parole complesse fonetiche.** Questo consente di ridurre al minimo e/o evitare le attivazioni false.

### <a name="peripherals"></a>Periferiche

Gli utenti possono interagire con l'app tramite le [periferiche](hardware-accessories.md). Le app non devono eseguire alcuna operazione speciale per sfruttare i vantaggi di questa funzionalità, tuttavia è opportuno verificare un paio di cose.
1. **Convalidare le interazioni personalizzate.** Elementi come i tasti di scelta rapida personalizzati per l'app.
2. **Convalida i tipi di input di cambio.** Tentativo di utilizzare più metodi di input per completare un'attività, ad esempio voce, movimento, mouse e tastiera, nello stesso scenario.

## <a name="system-integration"></a>Integrazione del sistema

### <a name="battery"></a>Batteria

Testare l'applicazione senza una fonte di alimentazione connessa per comprendere la velocità con cui svuota la batteria. Uno può facilmente comprendere lo stato della batteria esaminando le letture dei LED di alimentazione. 

![Stati del LED che indicano la potenza della batteria](images/batterypowerledindication-500px.png)<br>

*Stati del LED che indicano la potenza della batteria*

### <a name="power-state-transitions"></a>Transizioni di stato di alimentazione

Convalidare gli scenari principali funziona come previsto durante la transizione tra gli Stati di alimentazione. Ad esempio, l'applicazione rimane nella posizione originale? Lo stato viene mantenuto correttamente? Continua a funzionare come previsto?
1. **Standby/Riprendi.** Per attivare la modalità standby, è possibile premere e rilasciare immediatamente il pulsante di alimentazione. Il dispositivo verrà inoltre inserito automaticamente in standby dopo 3 minuti di inattività. Per riprendere dalla modalità standby, è possibile premere e rilasciare immediatamente il pulsante di alimentazione. Il dispositivo verrà ripreso anche se si connette o si disconnette da una fonte di alimentazione.
2. **Arresto/riavvio.** Per arrestarlo, premere e tenere premuto il pulsante di alimentazione per 6 secondi. Per riavviare, premere il pulsante di alimentazione.

### <a name="multi-app-scenarios"></a>Scenari con più app

Convalidare la funzionalità dell'app principale durante il cambio tra le app, soprattutto se è stata implementata un'attività in background. L'integrazione di copia/incolla e Cortana è utile anche per verificare se applicabile.

## <a name="telemetry"></a>Telemetria

Usare i dati di telemetria e l'analisi per guidare l'utente. L'integrazione di Analytics nell'app ti permette di ottenere informazioni dettagliate sull'app dai beta tester e dagli utenti finali. Questi dati possono essere usati per ottimizzare l'app prima dell'invio allo Store e per gli aggiornamenti futuri. Sono disponibili molte opzioni di analisi. Se non si è certi di dove iniziare, vedere [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Domande da considerare:
1. In che modo gli utenti usano lo spazio?
2. In che modo l'app posiziona gli oggetti nel mondo, è possibile rilevare i problemi?
3. Quanto tempo trascorre nelle diverse fasi dell'applicazione?
4. Quanto tempo trascorre nell'app?
5. Quali sono i percorsi di utilizzo più comuni che gli utenti stanno tentando?
6. Gli utenti stanno colpendo Stati e/o errori imprevisti?

## <a name="emulator-and-simulated-input"></a>Emulatore e input simulato

L' [emulatore di HoloLens](using-the-hololens-emulator.md) è un ottimo modo per testare in modo efficiente l'app olografica con un'ampia gamma di caratteristiche e spazi utente simulati. Ecco alcuni suggerimenti per usare efficacemente l'emulatore per testare l'app:
1. **Usare le chat virtuali dell'emulatore per espandere i test.** L'emulatore è dotato di un set di chat virtuali che è possibile usare per testare l'app in più ambienti.
2. **Usare l'emulatore per esaminare l'app da tutti gli angoli.** Le chiavi PageUp/PageDn rendono l'utente simulato più alto o più breve.
3. **Testare l'app con un HoloLens reale.** L'emulatore di HoloLens è un ottimo strumento che consente di eseguire rapidamente l'iterazione di un'app e di intercettare nuovi bug, ma assicurarsi di eseguire test anche su un HoloLens fisico prima di inviare a Windows Store. Questo è importante per garantire che le prestazioni e l'esperienza siano ottimali nell'hardware reale.

## <a name="automated-testing-with-perception-simulation"></a>Test automatizzati con simulazione della percezione

Alcuni sviluppatori di app potrebbero voler automatizzare il test delle proprie app. Oltre ai semplici unit test, è possibile usare lo stack di [simulazione della percezione](perception-simulation.md) in HoloLens per automatizzare gli input umani e internazionali nell'app. L'API di simulazione della percezione può inviare input simulato all'emulatore di HoloLens o a un HoloLens fisico.

## <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Per offrire all'app la possibilità di essere [pubblicata in Windows Store](submitting-an-app-to-the-microsoft-store.md), convalidarla e testarla localmente prima di inviarla per la certificazione. Se l'app è destinata al gruppo di dispositivi Windows. olografico, il [Kit di certificazione app Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) eseguirà solo i test di analisi statica locali nel PC. Nessun test verrà eseguito nella HoloLens.

## <a name="see-also"></a>Vedere anche
* [Invio di un'app a Windows Store](submitting-an-app-to-the-microsoft-store.md)
