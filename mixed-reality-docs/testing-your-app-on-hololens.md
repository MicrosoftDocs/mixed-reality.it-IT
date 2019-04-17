---
title: Test dell'app in HoloLens
description: Materiale sussidiario e suggerimenti per testare l'app di HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, test
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599973"
---
# <a name="testing-your-app-on-hololens"></a>Test dell'app in HoloLens

Test delle applicazioni di HoloLens sono molto simili a testare le applicazioni di Windows. Tutte le aree consuete devono essere considerate (funzionalità, l'interoperabilità, prestazioni, sicurezza, affidabilità e così via). Esistono, tuttavia, alcune aree che richiedono una gestione speciale o attenzione ai dettagli che non sono in genere osservato nell'App PC o telefono. Le app holographic devono eseguire senza problemi in un'ampia gamma di ambienti. Devono anche mantenere prestazioni comodità per l'utente in qualsiasi momento. Materiale sussidiario per il test di queste aree è descritta in dettaglio in questo argomento.

## <a name="performance"></a>Prestazioni

Le app holographic devono eseguire senza problemi in un'ampia gamma di ambienti. Devono anche mantenere prestazioni comodità per l'utente in qualsiasi momento. Le prestazioni sono molto importanti per l'esperienza dell'utente con un'app Holographic che abbiamo un intero argomento dedicato a esso. Assicurarsi leggere e seguire il [ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Test 3D in 3D
1. **Testare l'app in un numero di spazi diverso possibili.** Provare le chat del big data, stanze di piccole dimensioni, bagni, cucine, camere da letto, uffici, e così via. Considerare anche le funzionalità non standard, ad esempio walls non verticale, curve pareti, parte intera superiore non orizzontali stanze considerazione. Funziona bene quando la transizione tra le chat, pavimenti, passare attraverso corridoi o scale?
2. **Testare l'app in condizioni di illuminazione diversi.** Risponde correttamente alle diverse condizioni ambientali, ad esempio illuminazione, superfici nere trasparente/riflettente aree, ad esempio mirror pareti glass, e così via.
3. **Testare l'app in condizioni diverse movimento.** Inserire nel dispositivo e provare gli scenari in vari stati di movimento. Risponde correttamente a diversi o di stato stazionario?
4. **Testare il funzionamento dell'applicazione da diverse angolazioni.** Se si dispone di ologramma world bloccati, cosa accade se l'utente scorre sottostanti? Cosa accade se un elemento include tra l'utente e l'ologrammi? Cosa accade se l'utente esamina ologrammi sopra o sotto?
5. **Usare segnali audio e spaziali.** Assicurarsi che l'app Usa questi per impedire all'utente di perdersi.
6. **Testare l'app a diversi livelli di rumore ambientale.** Se è stato implementato comandi vocali, provare le richiama con diversi livelli di rumore ambientale.
7. **Prova le tue app seduto e permanente**. Assicurarsi di testare dai posti a sedere e le posizioni permanenti.
8. **Testare l'app da distanze diverse**. Elementi dell'interfaccia utente è possono essere letto e interagisce con essi da a portata di mano? Esegue il react app a utenti troppo vicino al recupero di vntana?
9. **Testare l'app con interazioni con le barre di app comuni**. Tutti i riquadri delle app e App universali 2D hanno una [barra dell'app](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) che consente di controllare il posizionamento dell'app nel mondo misto. Assicurarsi di fare clic su Rimuovi termina normalmente il processo dell'app e che il pulsante Indietro è supportato nel contesto di un'app universale di 2D. Provare a scalabilità e passaggio di un'app in [Adjust modalità](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) mentre è attiva e anche se è un riquadro dell'app sospese.

### <a name="environmental-test-matrix"></a>Matrice di Test ambientali

![Matrice di Test di ambiente per lo sviluppo di app di HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comfort
1. **Piani di ritaglio.** Essere accurata alla posizione in cui [vntana viene sottoposti a rendering](hologram-stability.md#hologram-render-distances).
2. **Evitare spostamenti virtuali coerenti con l'effettivo movimento della testina.** Evitare di spostare la fotocamera in modo che non è rappresentativo del movimento effettivo dell'utente. Se l'app richiede lo spostamento di utente attraverso una scena, rendere il movimento prevedibile, ridurre al minimo l'accelerazione e consentire all'utente di controllare il movimento.
3. **Seguire le linee guida sulla qualità di ologramma.** Le app ad alte prestazioni che implementano il [indicazioni di qualità ologrammi](hologram-stability.md) riducono le probabilità di causare disturbo utente.
4. **Distribuire vntana orizzontalmente anziché verticalmente.** L'utente di dedicare esteso i periodi di tempo a cercare o verso il basso può causare la fatica di collo.

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>Sguardo e movimenti

[Estasiati](gaze.md) è un form di base dell'input in HoloLens che consentono agli utenti di hanno lo scopo di ologrammi e l'ambiente. È possibile visivamente vedere in cui è destinato lo sguardo basati sulla posizione del cursore. È comune per associare il cursore sguardo a un cursore del mouse.

[I movimenti](gestures.md) sono modalità di interazione vntana, ad esempio un clic del mouse. La maggior parte dei casi i comportamenti di mouse e touch sono uguali, ma è importante comprendere e convalidare quando si differenziano.

**Convalida quando l'app ha un comportamento diverso con mouse e touch.** Per identificare eventuali incoerenze e aiutare nelle decisioni di progettazione per rendere l'esperienza più naturale per gli utenti. Ad esempio, attivare un'azione in base al passaggio del mouse.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

### <a name="custom-voice-commands"></a>Comandi vocali personalizzati

[Input vocale](voice-input.md) è una forma naturale di interazione. L'esperienza utente possibile magici o confusione a seconda della scelta dei comandi e come è possibile esporli. Di norma, è necessario non utilizzare comandi vocali di sistema, ad esempio "Select" o "Ehi Cortana" come comandi personalizzati. Ecco alcuni aspetti da considerare:
1. **Evitare di usare i comandi con un suono simili.** Questo potenzialmente può attivare il comando non corretto.
2. **Scegliere Avanzate alla fonetica parole quando possibile.** Questo sarà ridurre a icona e/o evitare false attivazioni.

### <a name="peripherals"></a>Periferiche

Gli utenti possono interagire con l'App tramite [periferiche](hardware-accessories.md). Le app non devono eseguire alcuna operazione particolare per sfruttare i vantaggi di tale funzionalità, tuttavia, esistono un paio di cose opportuno verificare.
1. **Convalidare le interazioni personalizzate.** Elementi quali i tasti di scelta rapida da tastiera personalizzato per l'app.
2. **Convalidare il passaggio di tipi di input.** È stato effettuato un tentativo di usare più metodi di input per completare un'attività, ad esempio voce, movimento, mouse e tastiera tutti nello stesso scenario.

## <a name="system-integration"></a>Integrazione di sistemi

### <a name="battery"></a>Batteria

Testare l'applicazione senza una fonte di alimentazione connessa per comprendere la rapidità diamo la batteria. Uno può comprenderne facilmente lo stato della batteria, esaminando le letture LED di alimentazione. ![Condizioni dei LED che indicano l'alimentazione a batteria](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>Transizioni di stato di alimentazione

Convalidare gli scenari principali lavoro come previsto durante la transizione tra stati di alimentazione. Ad esempio, l'applicazione rimane nella posizione originale? Corretto mantenuta lo stato? Questo continuerà a funzionare come previsto?
1. **Standby / ripresa.** Per entrare in modalità standby, è possibile premere e rilasciare il pulsante di alimentazione immediatamente. Il dispositivo verrà anche immettere standby automaticamente dopo 3 minuti di inattività. Per riprendere dalla modalità standby, è possibile premere e rilasciare il pulsante di alimentazione immediatamente. Il dispositivo verrà ripreso anche se si connettono o disconnessione, da una fonte di alimentazione.
2. **Arresto / riavvio.** L'arresto, premere e tenere premuto il pulsante di alimentazione continuamente per 6 secondi. Per riavviare, premere il pulsante di alimentazione.

### <a name="multi-app-scenarios"></a>Scenari con più App

Convalidare la funzionalità di app di base quando si passa tra le app, soprattutto se è stata implementata un'attività in background. Integrazione di Cortana e Copia/Incolla sono inoltre opportuno verificare dove applicabile.

## <a name="telemetry"></a>Telemetria

Usare i dati di telemetria e analitica per ottenere istruzioni utili. L'integrazione analitica nella tua app consentirà di ottenere informazioni dettagliate sull'applicazione dai Beta tester e utenti finali. Questi dati sono utilizzabile per ottimizzare l'app prima dell'invio di Store e per gli aggiornamenti futuri. Sono disponibili molte opzioni di analitica disponibili. Se non si conosce dove iniziare, consultare [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Domande da considerare:
1. Modo gli utenti usano lo spazio?
2. Come è l'app per l'inserimento di oggetti nel mondo - è possibile rilevare i problemi?
3. Quanto tempo si trascorre in fasi diverse dell'applicazione?
4. Quanto tempo si trascorre nell'app?
5. Quali sono i percorsi di uso più comuni gli utenti sta cercando?
6. Gli utenti raggiungono gli stati imprevisti e/o errori?

## <a name="emulator-and-simulated-input"></a>Emulatore e Input simulato

Il [HoloLens emulatore](using-the-hololens-emulator.md) è un ottimo modo per testare in modo efficiente la tua applicazione Holographic con un'ampia gamma di caratteristiche a utente simulato e spazi. Di seguito sono riportati alcuni suggerimenti per l'uso in modo efficace l'emulatore per testare l'app:
1. **Usano le chat room virtuale dell'emulatore per espandere l'attività di test.** L'emulatore include un set di sale virtuali che è possibile usare per testare l'app in ambienti ulteriormente.
2. **Usare l'emulatore per osservare l'app da tutti gli angoli.** I tasti PGSU/PageDn renderà l'utente simulato o più bassa.
3. **Testare l'app con una reale HoloLens.** L'emulatore di HoloLens è uno strumento straordinario per aumentare rapidamente l'iterazione in un'app e individuare i bug nuove, ma è importante anche testare su un HoloLens fisico prima dell'invio ad di Windows Store. Questo è importante per garantire che le prestazioni e sono ideali sulll'hardware effettivo.

## <a name="automated-testing-with-perception-simulation"></a>Test automatici con Perception simulazione

Alcuni sviluppatori di app potrebbero voler automatizzare i test delle proprie app. Oltre semplice unit test, è possibile usare la [simulazione percezione](perception-simulation.md) stack in HoloLens automatizzare umani e world input all'app. L'API di simulazione di perception possibile inviare input simulato per l'emulatore di HoloLens o un HoloLens fisico.

## <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Per assegnare all'app le maggiori probabilità di essere [pubblicate in di Windows Store](submitting-an-app-to-the-microsoft-store.md), convalidare e testarla localmente prima di inviarla per la certificazione. Se l'app è destinata la famiglia di dispositivi Windows.Holographic, il [Kit di certificazione App Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) verrà eseguito solo i test di analisi statica locale nel PC. Non ci sono test verrà eseguito su di HoloLens.

## <a name="see-also"></a>Vedere anche
* [Invio di un'app di Windows Store](submitting-an-app-to-the-microsoft-store.md)
