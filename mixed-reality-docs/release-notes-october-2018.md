---
title: Note sulla versione - ottobre 2018
description: HoloLens e note sulla versione di realtà mista di Windows per Windows 10 ottobre 2018 Update (noto anche come RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: release notes, versione, windows 10, build, rs5, sistema operativo
ms.openlocfilehash: 9838b4dcbdedc4bf2c94a8e31f3f8eb4c9634d36
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604163"
---
# <a name="release-notes---october-2018"></a>Note sulla versione - ottobre 2018

Il **[Windows 10 ottobre 2018 Update](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (noto anche come RS5) include nuove funzionalità per HoloLens e realtà mista di Windows auricolari immersive connesso al PC. 

Per aggiornare la versione più recente di HoloLens o un PC (per auricolari (VR) coinvolgenti di realtà mista di Windows), aprire il **le impostazioni** app e passare alla **aggiornamento e sicurezza**, quindi selezionare il **cercare gli aggiornamenti** pulsante. In un PC Windows 10, è anche possibile installare manualmente Windows 10 ottobre 2018 Update usando le [strumento di creazione dei supporti Windows](https://www.microsoft.com/software-download/windows10).

**Versione più recente per Desktop:** Windows 10 October 2018 Update (**10.0.17763.107**)<br>
**Versione più recente per HoloLens:** Windows 10 October 2018 Update (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per le cuffie coinvolgenti di realtà mista di Windows

Windows 10 ottobre 2018 Update include numerosi miglioramenti per l'uso auricolari (VR) coinvolgenti di realtà mista di Windows con il PC desktop.

### <a name="for-everyone"></a>Per tutti gli utenti

* **Torcia realtà mista** : aprire un portale nel mondo reale per individuare la tastiera, vedere qualcuno nelle vicinanze o esaminare l'ambiente circostante senza rimuovere le cuffie! È possibile attivare torcia realtà mista dal menu Start, premere Windows + i quadratini di ridimensionamento sul controller di movimento o pronunciando "Torcia on/off". Scegliere il controller nella direzione di ciò che si desidera visualizzare, come l'uso di un torcia al buio.

    ![Realtà mista torcia](images/mr-flashlight.png)

* **Nuove app e sui modi per avviare il contenuto di realtà mista home**
    * Se si usa [realtà mista di Windows per SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), i titoli SteamVR ora visualizzati nel menu Start e nelle schermate di avvio di app per ognuna può essere inserite in realtà mista home.
    
        ![Nelle schermate di avvio app SteamVR](images/steamvr-launchers.png)
        
    * Nuove *360 video* app per l'individuazione di una selezione regolarmente curato di video a 360 gradi.
    * Nuove *WebVR Showcase* esperienze di app per l'individuazione di una selezione di WebVR curato regolarmente.
    * I clienti di realtà mista di Windows prima volta immettere il Cliff House e trovare che prepopolata con utilità di avvio app 3D per alcuni dei nostri giochi da di Microsoft Store e App immersive preferite.
    * Windows di Microsoft Edge includono ora un *condivisione* pulsante.
* **Menu Azioni rapide** -dall'interno di un'app di realtà mista coinvolgenti, è possibile premere il pulsante di Windows per accedere a un nuovo menu Azioni rapide, accesso facile ai *menu SteamVR*, *acquisizione di foto/video*, *torcia*, e *domestica*.
* **Supporto per i PC zaino** -realtà mista di Windows eseguire immersive auricolari (VR) in zaino PC senza richiedere un emulatore di visualizzazione dopo aver completato il programma di installazione.
* **Nuove funzionalità audio** -è ora possibile eseguire il mirroring audio da un'esperienza di realtà mista di Windows sia l'audio jack (o le cuffie) nelle cuffie *e* un dispositivo audio connesso al PC (ad esempio altoparlanti esterni). Nella visualizzazione della cuffia, sono stati anche aggiunti un indicatore visivo per il livello di volume.
* **Altri miglioramenti**
    * Aggiornamenti del portale di realtà misti vengono ora forniti tramite il Microsoft Store, attivazione più veloce degli aggiornamenti tra versioni principali di Windows. Si noti che questo vale solo per l'app desktop e l'esperienza di visore VR realtà mista di Windows è ancora aggiornato con il sistema operativo. 
    * Quando auricolari passare alla modalità sospensione, le app di realtà mista di Windows vengono sospesi invece di terminazione (fino a quando non è stato chiuso il portale di realtà mista).
    
### <a name="for-developers"></a>Per sviluppatori

* **[Codice a matrice di rilevamento](qr-code-tracking.md)**  -eseguire il codice a matrice di abilitare la registrazione nell'app per realtà mista, consentendo auricolari (VR) coinvolgenti di realtà mista di Windows cercare i codici a matrice e li inserisce in App interessate.
* **Hardware DRM supporto per le app immersive** -gli sviluppatori possono le trame di hardware protetto quaterna richiesta ora se supportata dall'hardware di visualizzazione, che consente alle applicazioni di utilizzare contenuti protetti con RMS hardware da origini, ad esempio PlayReady.
* **[Integrare realtà mista acquisizione dell'interfaccia utente nelle applicazioni coinvolgenti](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  -gli sviluppatori possono integrare l'acquisizione di realtà mista nelle App utilizzando il Windows incorporato [acquisizione con fotocamera UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) con solo poche righe di codice.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

Il 10 ottobre 2018 di Windows Update è disponibile pubblicamente per tutti i clienti di HoloLens e include una serie di miglioramenti, ad esempio:

### <a name="for-everyone"></a>Per tutti gli utenti

* **Menu Azioni rapide** -dall'interno di un'app di realtà mista coinvolgenti, è possibile premere il pulsante di Windows per accedere a un nuovo menu Azioni rapide, accesso facile ai *avvia la registrazione di video*, *scattare fotografie*, *Home page di realtà mista*, *modificare il volume*, e *Connect*.
* **Avvio/arresto acquisizione video dall'inizio o dal menu Azioni rapide** -se si avvia acquisizione video dal menu Start o dal menu Azioni rapide, sarà in grado di arrestare la registrazione dalla stessa posizione. (Non dimenticare, è possibile eseguire sempre questa operazione con i comandi vocali troppo.)
* **Progetto per un dispositivo abilitato per Miracast** -il contenuto di HoloLens a un dispositivo Surface nelle vicinanze o TV o monitor del progetto se si usa una visualizzazione abilitato per Miracast o una scheda.
* **Nuove notifiche** -visualizzazione e rispondere alle notifiche su HoloLens, proprio come in un PC.  
* **Le sovrimpressioni utili nelle app di realtà mista immersive** -si vedrà ora sovrapposizioni, ad esempio la tastiera, le finestre di dialogo, selezione dei file, e così via, quando si usa immersive mista le App per realtà.
* **Indicatore visivo per la modifica volume** : quando si usa il volume di / sui pulsanti nella finestra di HoloLens, verrà visualizzato un indicatore visivo del livello di volume nelle cuffie.
* **Nuovi oggetti visivi per l'avvio di dispositivo** -è stato aggiunto un indicatore di caricamento durante il processo di avvio per fornire un feedback visivo che il sistema sta caricando.
* **Tenerlo a portata di condivisione** -esperienza di Windows nelle vicinanze la condivisione consente di condividere un'acquisizione con un dispositivo nelle vicinanze di Windows.  
* **Condivisione da Microsoft Edge** -Microsoft Edge include ora una *condivisione* pulsante. 

### <a name="for-developers"></a>Per sviluppatori

* **[Integrare realtà mista acquisizione dell'interfaccia utente nelle applicazioni coinvolgenti](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  -gli sviluppatori possono integrare l'acquisizione di realtà mista nelle App utilizzando il Windows incorporato [acquisizione con fotocamera UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) con solo poche righe di codice.

### <a name="for-commercial-customers"></a>Per i clienti commerciali

* **Abilitare il provisioning di post-installazione** -è ora possibile applicare un pacchetto di provisioning in qualsiasi momento usando le impostazioni di runtime.
* **Assegnato l'accesso con gruppi di Azure AD** -è ora possibile usare gruppi di Azure AD per la configurazione di Windows assegnato l'accesso per impostare la configurazione per chiosco multimediale uno o più app.
* **AGGIUNGERE sign-nel commutatore profilo dalla schermata di accesso** -PIN-Accedi a questo punto sono disponibile per "Altro utente" nella schermata di accesso. 
* **Accedere con il Provider di credenziali Web mediante password** -è ora possibile selezionare l'icona del mondo per avviare web Accedi con la password. 
* **Leggere le informazioni hardware dispositivo tramite MDM** -gli amministratori IT possono vedere e registrare HoloLens in numero di serie di dispositivi nella console MDM.
* **Impostare il nome di dispositivo HoloLens tramite MDM (Rinomina)** -gli amministratori IT possono vedere e rinominare i dispositivi HoloLens nella console MDM.

### <a name="for-international-customers"></a>Per i clienti internazionali

È ora possibile usare HoloLens con interfaccia utente localizzata per il cinese semplificato o giapponese, tra cui tastiera Pinyin localizzata, dettatura, sintesi vocale e comandi vocali.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'eccezionale esperienza di realtà mista di Windows, ma ancora Microsoft eseguita verificando alcuni problemi noti. Se si trova ad altri utenti, please [commenti e suggerimenti](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Dopo l'aggiornamento
È possibile notare i seguenti problemi quando con Windows 10 ottobre 2018 Aggiorna nella finestra di HoloLens:
* **Le app possono finire in accesso ciclico quando sono avviate da una notifica** – alcune App che richiedono accesso possibile fine-up in un accesso ciclo infinito quando avviata da una notifica. Ad esempio, questa situazione può verificarsi dopo aver installato l'app portale aziendale di Microsoft da di Microsoft Store e averlo avviato da una notifica di completamento l'installazione.
* **App nella pagina di accesso può essere completata con una pagina vuota** : In alcuni casi in cui viene illustrata una richiesta di accesso tramite l'applicazione, al termine, la pagina di accesso non viene chiusa e Mostra una pagina vuota (nera). È possibile chiudere la pagina vuota o spostarlo per individuare l'applicazione sottostante. Ad esempio, questa situazione può verificarsi in fase di accesso durante la registrazione MDM dall'app impostazioni. 

## <a name="provide-feedback-and-report-issues"></a>Fornire commenti e suggerimenti e segnalare problemi

Usare la [app di Hub di commenti e suggerimenti sul PC Windows 10 o HoloLens](give-us-feedback.md) per fornire commenti e suggerimenti e segnalare problemi. Con Hub di Feedback garantisce che tutte le informazioni di diagnostica necessarie sono incluse per consentire ai nostri tecnici rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si vuole che Hub di commenti e suggerimenti per accedere alla cartella documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto visore VR immersivi (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Supporto di HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](install-the-tools.md)
* [Invia commenti e suggerimenti](give-us-feedback.md)

