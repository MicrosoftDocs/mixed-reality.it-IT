---
title: Note sulla versione - ottobre 2017
description: Note sulla versione di realtà mista di Windows per il Windows 10 Fall Creators Update (ottobre 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: release notes, versione, windows 10, build, rs3, sistema operativo
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597832"
---
# <a name="release-notes---october-2017"></a>Note sulla versione - ottobre 2017

Introduzione a Windows di realtà mista. La versione del **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduce il supporto per i nuovi [auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) e [i controller di movimento ](motion-controllers.md), che consente di esplorare nuovi scenari, giocare VR ed esperienza coinvolgente e concreto quando si è connessi a un [realtà mista di Windows in grado di supportare PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

La versione del controller di movimento e auricolari realtà mista di Windows è il risultato di un impegno del team di grandi dimensioni e un importante passo avanti per la [piattaforma di realtà mista di Windows](mixed-reality.md), che include [Microsoft HoloLens](hololens-hardware-details.md). Mentre HoloLens non viene ricevuto un aggiornamento con il rilascio di Windows 10 Fall Creators Update, sa che non è ancora arrestato lavoro su HoloLens; avremo molti approfondimenti e informazioni dettagliate da applicare le attività più recenti in realtà mista di Windows nel suo complesso. In effetti, auricolari coinvolgenti di realtà mista di Windows e movimento controller rappresentano un'ottima voce punto troppo, come le stesse API, strumenti, allo sviluppo per HoloLens e i concetti si applicano a entrambe.

Per aggiornare la versione più recente per ogni dispositivo, aprire il **le impostazioni** app e passare alla **aggiornamento e sicurezza**, quindi selezionare il **Controlla aggiornamenti** pulsante. In un PC Windows 10, è anche possibile installare manualmente l'utilizzo di Windows 10 Fall Creators Update il [strumento di creazione dei supporti Windows](https://www.microsoft.com/software-download/windows10).

 **Versione più recente per Desktop:** Windows 10 Desktop, ottobre 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Versione più recente per HoloLens:** [Windows 10 Holographic agosto 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Anniversary Update)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introduzione a realtà mista di Windows

I di Windows 10 Fall Creators Update introduce ufficialmente il supporto per auricolari realtà mista di Windows e i controller di movimento, nonché rendere primo sistema operativo spaziali del mondo Windows 10. Ecco le novità:
* **[Ampia gamma di auricolari](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)**  -realtà mista di Windows è consentendo ai partner di offrire un'ampia gamma di auricolari quale inizio a 399 USD in bundle con i controller di movimento.
* **[I controller di movimento](motion-controllers.md)**  -controller movimento di realtà mista di Windows in modalità wireless associa a PC tramite Bluetooth e sei gradi di libertà di rilevamento, una vasta gamma di metodi di input e IMUs di funzionalità.
* **[Semplice installazione e la portabilità](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)**  - impostare configurare e iniziare in meno di 10 minuti. Auricolari immersive utilizzano il rilevamento interno a esterno per tenere traccia del movimento e i controller di movimento, con sei gradi di libertà. Nessun fotocamere esterni o marcatori faro necessari!
* **[Supporto per un intervallo più ampio di PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)**  -realtà mista di Windows consentirà di altre persone a esperienza desktop VR rispetto al passato, con supporto per selezionare integrato schede grafiche e PC a partire a 499 USD.
* **[Realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md)**  -primo sistema operativo spaziali del mondo offre un ambiente home familiare per il multitasking con App 2D, giochi di realtà virtuale che esegue l'applicazione e le App e il posizionamento vntana decorativa.
* **[Straordinari giochi di realtà virtuale e le app di Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)**  - di intrattenimento, ad esempio Hulu VR e 360 video ai giochi POEMA epico, ad esempio SUPERHOT VR e il sole Arizona, di Microsoft Store è un intervallo di esperienza in Windows Mixed contenuto Realtà.
* **[Accesso anticipato SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)**  : di Windows 10 Fall Creators Update Abilita il supporto per i titoli SteamVR da riprodurre con auricolari realtà mista di Windows e i controller, rendendo il catalogo più grande di VR titoli disponibili per Windows misti Utenti di realtà.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'eccezionale esperienza di realtà mista di Windows, ma ancora Microsoft eseguita verificando alcuni problemi noti. Se si trova ad altri utenti, please [commenti e suggerimenti](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop in casa la realtà mista di Windows
* Strumento di cattura non funziona nelle app Desktop.
* App desktop non viene mantenuta l'impostazione al riavvio.
* Se si Usa anteprima del portale di realtà mista sul desktop, quando si apre l'app Desktop in casa la realtà mista di Windows, è possibile notare l'effetto di mirror infinito. 
* L'esecuzione dell'app Desktop può causare problemi di prestazioni sul non - extra misto realtà i PC Windows; non è consigliabile.  
* App desktop può avviare automaticamente perché una finestra invisibile nel Desktop ha lo stato attivo. 
* Controllo dell'Account utente desktop prompt renderà le cuffie, possono visualizzare nero fino a quando non viene completato il prompt dei comandi.

### <a name="windows-mixed-reality-setup"></a>Programma di installazione di realtà mista di Windows
* Quando si configura Windows con le cuffie connessa, il monitor del PC diventi vuoto. Disconnettere le cuffie per abilitare l'output per il monitor del PC per completare l'installazione di Windows.
* Quando si crea un limite, la traccia potrebbe non riuscire. In questo caso, ripetere l'operazione, come il sistema verrà fornite ulteriori informazioni lo spazio nel corso del tempo.
* Se si abilita Cortana o disattivare durante l'installazione di realtà mista di Windows, questa modifica verrà applicata alle impostazioni di desktop Cortana.
* Se non hai le cuffie connessi, si potrebbero perdere suggerimenti aggiuntivi quando si visita prima la realtà mista di Windows home.
* Bluetooth le cuffie possono causare l'interferenza con i controller di movimento. È consigliabile associazione annullamento o spegnere controller Bluetooth durante le sessioni di realtà mista di Windows.

### <a name="games-and-apps-from-windows-store"></a>Giochi e App da Windows Store
* Alcuni giochi a grafica intensiva, ad esempio Forza Motorsports 6, potrebbero causare problemi di prestazioni nei PC in grado di supportare meno durante la riproduzione in realtà mista di Windows.

### <a name="audio"></a>Audio
* Come indicato in precedenza, periferiche Bluetooth Audio non funzionano bene con voice di realtà mista di Windows e le esperienze di audio spaziale. Si può anche influire negativamente sull'esperienza di controller di movimento. Non è consigliabile utilizzare auricolari Bluetooth Audio con realtà mista di Windows.
* Non è possibile utilizzare il dispositivo connesso a audio (o parte del) le cuffie per la riproduzione audio quando il dispositivo non è indossato. Se si ha solo un auricolare audio, è possibile connettere le cuffie audio per il PC host anziché le cuffie. Se, pertanto, quindi è necessario disattivare "commutatore per audio visore VR" **le impostazioni** > **realtà mista** > **Audio e vocale**.
* Alcune applicazioni, inclusi molti di questi avviate tramite SteamVR, possono perdere audio o un blocco quando il dispositivo audio viene modificato quando si avvia o arresta il portale di realtà mista. Dopo avere aperto l'app del portale di realtà mista per risolvere il problema, riavviare l'app.
* Se si dispone di Cortana abilitata nell'host di PC prima di utilizzare il visore VR realtà mista di Windows, si potrebbe perdere la simulazione spaziale audio applicata alle App che utilizzare per racchiudere la realtà mista di Windows home. La soluzione alternativa consiste nell'abilitare "Windows Sonic per le cuffie" in tutti i dispositivi audio associati al computer, anche le cuffie audio dispositivo connesso:
   1. Fare clic sull'icona dell'altoparlante della barra delle applicazioni desktop e selezionare dall'elenco dei dispositivi audio.
   2. Fare doppio clic sull'icona dell'altoparlante della barra delle applicazioni desktop e selezionare "Windows Sonic per le cuffie" nel menu "L'installazione dell'altoparlante".
   3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
>[!NOTE]
> - Poiché le cuffie/relatori connesse per le cuffie non sarà più visualizzato a meno che non si sta usura si, è necessario eseguire questa operazione dalla finestra dell'applicazione Desktop nella realtà mista di Windows home per applicare questa impostazione per il dispositivo audio è connesso alle cuffie (o integrato nelle cuffie).
> - Un'altra opzione consiste nel disattivare "Cortana ti permettono di rispondere a Ehi Cortana" nella **le impostazioni** > **Cortana** sul desktop prima dell'avvio di realtà mista di Windows.

* Quando un altro dispositivo USB multimediale (ad esempio una webcam) condivide lo stesso hub USB (esterno o all'interno del PC) con il visore VR realtà mista di Windows, in casi rari audio jack/cuffie della cuffia potrebbe disporre di un suono apparizione oppure nessun audio affatto. È possibile risolvere il problema per le cuffie in una porta USB che non condividono lo stesso hub come l'altro dispositivo o disconnettere o disabilitare l'altro dispositivo USB multimediale.
* In rari casi, è possibile notare un picco di rumore dalle cuffie connessa per le cuffie hub USB del computer host non può fornire potenza sufficiente per il visore VR realtà mista di Windows.

### <a name="speech"></a>Comandi vocali
* Cortana potrebbe non riuscire a riprodurre il segnali acustici per le risposte di audio e in attesa/pensare ai comandi.
* Cortana nei mercati Cina e Giappone non vengono correttamente visualizzati testo sotto il controllo circle Cortana durante l'utilizzo.
* Cortana può risultare lenta la prima volta che viene richiamata in una sessione del portale di realtà mista. Può risolvere il problema effettuando che "Cortana ti permettono di" rispondere a Ehi Cortana sotto **le impostazioni** > **Cortana** > **comunicare con Cortana** è abilitata.
* Cortana possono essere eseguite più lentamente nei PC Windows Mixed Reality Ultra dai PC.
* Quando i tasti di sistema sono impostato su una lingua diversa dalla lingua dell'interfaccia utente in realtà mista di Windows, utilizzando la dettatura da tastiera in realtà mista di Windows comporterà una finestra di dialogo di errore sulla dettatura non funziona perché non è disponibile la connessione Wi-Fi. Per risolvere il problema è sufficiente verificare che la lingua della tastiera di sistema corrispondente alla lingua interfaccia utente di realtà mista di Windows.
* Spagna non è correttamente viene riconosciuta come un mercato in cui vocale è abilitata per realtà mista di Windows.

### <a name="holograms"></a>Ologrammi
* Se è stato immesso un numero elevato di vntana nella home di realtà mista di Windows, alcuni possono scomparsa e come Guardatevi intorno. Per evitare questo problema, rimuovere alcuni del vntana in tale area della realtà mista di Windows home.

### <a name="motion-controllers"></a>Controller di movimento
* In alcuni casi, se fa clic su una pagina Web in Microsoft Edge, il contenuto verrà ingrandire anziché fare clic su.
* In alcuni casi quando si fa clic su un collegamento in Microsoft Edge, la selezione non funzionerà.

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto visore VR immersivi (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemi noti di HoloLens](hololens-known-issues.md)
* [Installare gli strumenti](install-the-tools.md)
* [Invia commenti e suggerimenti](give-us-feedback.md)
