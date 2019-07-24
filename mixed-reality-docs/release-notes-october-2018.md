---
title: Note sulla versione-2018 ottobre
description: Note sulla versione di HoloLens e Windows Mixed Reality per l'aggiornamento di Windows 10 ottobre 2018 (noto anche come RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: Note sulla versione, versione, Windows 10, Build, RS5, sistema operativo
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524245"
---
# <a name="release-notes---october-2018"></a>Note sulla versione-2018 ottobre

L' **[aggiornamento di Windows 10 ottobre 2018](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (noto anche come RS5) include nuove funzionalità sia per gli auricolari HoloLens che per quelli immersivi con la realtà mista di Windows connessi ai PC. 

Per eseguire l'aggiornamento alla versione più recente di HoloLens o PC (per auricolari (VR) Windows Mixed Reality (VR), aprire l'app **Impostazioni** , passare a **Aggiorna & sicurezza**, quindi selezionare il pulsante **Controlla aggiornamenti** . In un PC Windows 10, è anche possibile installare manualmente l'aggiornamento di Windows 10 ottobre 2018 usando lo [strumento di creazione di Windows Media](https://www.microsoft.com/software-download/windows10).

**Versione più recente per desktop:** Aggiornamento di Windows 10 ottobre 2018 (**10.0.17763.107**)<br>
**Versione più recente per HoloLens:** Aggiornamento di Windows 10 ottobre 2018 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per gli auricolari immersivi a realtà mista di Windows

L'aggiornamento di Windows 10 ottobre 2018 include numerosi miglioramenti per l'uso di auricolari di Windows misto Reality (VR) con il PC desktop.

### <a name="for-everyone"></a>Per tutti

* **Torcia realtà mista** : consente di aprire un portale nel mondo reale per trovare la tastiera, vedere qualcuno vicino o esaminare l'ambiente circostante senza rimuovere l'auricolare. È possibile attivare la torcia a realtà mista dal menu Start, premendo Windows + Acquisisci sul controller di movimento o dicendo "torcia acceso/spento". Puntare il controller nella direzione di ciò che si vuole visualizzare, ad esempio usando una torcia elettrica.

    ![Torcia realtà mista](images/mr-flashlight.png)

* **Nuove app e modi per avviare il contenuto nella Home realtà mista**
    * Se si usa la [realtà mista di Windows per SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), i titoli di SteamVR ora vengono visualizzati nel menu Start e i lanci di app per ognuno di essi possono essere inseriti nella Home realtà mista.
    
        ![SteamVR di avvio delle app](images/steamvr-launchers.png)
        
    * Nuova app *video di 360* per l'individuazione di una selezione di video di 360 gradi con regolarità.
    * Nuova app *WebVR Showcase* per l'individuazione di una selezione regolare di esperienze WebVR.
    * I primi clienti con la realtà mista di Windows entrano a Cliff House e li trovano già popolati con i lanci di app 3D per alcune delle app e dei giochi immersivi Preferiti dal Microsoft Store.
    * Microsoft Edge Windows include ora un pulsante *Condividi* .
* **Menu azioni rapide** : dall'interno di un'app immersiva mista, è possibile premere il pulsante Windows per accedere a un nuovo menu azioni rapide, con accesso semplice a *SteamVR menu*, *acquisizione foto/video*, *torcia elettrica*e *Home*.
* **Supporto per i PC zaino** : gli auricolari a realtà mista (VR) di Windows vengono eseguiti nei PC Backpack senza richiedere un emulatore di visualizzazione una volta completata l'installazione.
* **Nuove funzionalità audio** : è ora possibile eseguire il mirroring dell'audio da un'esperienza di realtà mista di Windows sia al jack audio (o alle cuffie) nell'auricolare *che* a un dispositivo audio connesso al PC (ad esempio, altoparlanti esterni). È stato inoltre aggiunto un indicatore visivo per il livello di volume nella visualizzazione dell'auricolare.
* **Altri miglioramenti**
    * Gli aggiornamenti del portale di realtà mista vengono ora distribuiti attraverso la Microsoft Store, consentendo aggiornamenti più rapidi tra le versioni principali di Windows. Si noti che questo vale solo per l'app desktop e l'esperienza con l'auricolare della realtà mista di Windows continua ad aggiornarsi con il sistema operativo. 
    * Quando le cuffie passano alla modalità sospensione, le app per la realtà mista di Windows vengono sospese anziché terminate (fino alla chiusura del portale di realtà mista).
    
### <a name="for-developers"></a>Per sviluppatori

* **[Rilevamento del codice](qr-code-tracking.md)** a matrice: è possibile abilitare il rilevamento del codice a matrice nell'app per realtà mista, consentendo l'uso di auricolari di Windows mista (VR) per la ricerca di codici QR e la segnalazione delle app interessate.
* **Supporto DRM hardware per le app immersive** : gli sviluppatori possono ora richiedere trame con buffer protetti da hardware se supportate dall'hardware di visualizzazione, consentendo alle applicazioni di usare contenuto protetto da hardware da origini come PlayReady.
* **[Integrare l'interfaccia utente di acquisizione di realtà mista in app immersive](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** : gli sviluppatori possono integrare l'acquisizione di realtà mista nelle app usando l' [interfaccia utente](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) predefinita di acquisizione della fotocamera Windows con poche righe di codice.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

L'aggiornamento di Windows 10 ottobre 2018 è disponibile pubblicamente per tutti i clienti di HoloLens e include una serie di miglioramenti, ad esempio:

### <a name="for-everyone"></a>Per tutti

* **Menu azioni rapide** : dall'interno di un'app immersiva mista, è possibile premere il pulsante Windows per accedere a un nuovo menu azioni rapide, con facile accesso per *iniziare a registrare video*, *scattare foto*, *Home realtà mista*, *modificare volume*e *Connect*.
* **Avviare/arrestare l'acquisizione video dal menu azioni rapide o avvio** : se si avvia l'acquisizione video dal menu Start o dal menu azioni rapide, sarà possibile arrestare la registrazione dalla stessa posizione. Non dimenticare che è sempre possibile eseguire questa operazione con i comandi vocali.
* **Proiettare in un dispositivo abilitato per Miracast** : proiettare il contenuto di HoloLens su un dispositivo Surface o TV/monitor con supporto per Miracast.
* **Nuove notifiche** : consente di visualizzare e rispondere alle notifiche in HoloLens, proprio come in un PC.  
* **Sovrapposizioni utili nelle app immersive per realtà mista** : ora è possibile visualizzare sovrapposizioni come tastiera, finestre di dialogo, selezione file e così via quando si usano app di realtà miste immersive.
* **Indicatore visivo per la modifica del volume** : quando si usano i pulsanti di scorrimento del volume in HoloLens, viene visualizzato un indicatore visivo del livello del volume nell'auricolare.
* **Nuovi oggetti visivi per l'avvio del dispositivo** : è stato aggiunto un indicatore di caricamento durante il processo di avvio per fornire il feedback visivo che il sistema sta caricando.
* **Condivisione vicina** : l'esperienza di condivisione vicina a Windows consente di condividere un'acquisizione con un dispositivo Windows più vicino.  
* **Condividi da Microsoft Edge** : Microsoft Edge include ora un pulsante *Condividi* . 

### <a name="for-developers"></a>Per sviluppatori

* **[Integrare l'interfaccia utente di acquisizione di realtà mista in app immersive](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** : gli sviluppatori possono integrare l'acquisizione di realtà mista nelle app usando l' [interfaccia utente](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) predefinita di acquisizione della fotocamera Windows con poche righe di codice.

### <a name="for-commercial-customers"></a>Per i clienti commerciali

* **Abilitare il provisioning post-installazione** : è ora possibile applicare un pacchetto di provisioning di runtime in qualsiasi momento usando le impostazioni.
* **Accesso assegnato con gruppi di Azure ad** : è ora possibile usare i gruppi di Azure ad per la configurazione dell'accesso assegnato a Windows per configurare la configurazione del chiosco multimediale a più app o a più app.
* **Aggiunta dell'accesso all'opzione del profilo dalla schermata di accesso** . l'accesso PIN è ora disponibile per "altro utente" nella schermata di accesso. 
* **Leggere le informazioni sull'hardware del dispositivo tramite MDM** : gli amministratori IT possono visualizzare e tenere traccia di HoloLens in base al numero di serie del dispositivo nella console MDM.
* **Impostare il nome del dispositivo HoloLens tramite MDM (Rinomina)** : gli amministratori IT possono visualizzare e rinominare i dispositivi HoloLens nella console MDM.

### <a name="for-international-customers"></a>Per i clienti internazionali

È ora possibile usare HoloLens con l'interfaccia utente localizzata per il cinese semplificato o giapponese, tra cui la tastiera, la dettatura, la sintesi vocale e i comandi vocali.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato duramente per offrire un'eccezionale esperienza di realtà mista di Windows, ma stiamo ancora verificando alcuni problemi noti. Se si trovano altre persone, inviare [commenti e suggerimenti](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Dopo l'aggiornamento
È possibile che si verifichino i seguenti problemi quando si usa l'aggiornamento di Windows 10 ottobre 2018 in HoloLens:
* Le **app possono finire nel ciclo di accesso quando vengono avviate da una notifica** . alcune app che richiedono l'accesso possono terminare con un ciclo di accesso infinito quando vengono avviate da una notifica. Questo può verificarsi, ad esempio, dopo l'installazione dell'app Microsoft Portale aziendale dal Microsoft Store e l'avvio dalla notifica di completamento dell'installazione.
* La **pagina di accesso dell'app può essere completata con una pagina vuota** : in alcuni casi, quando viene visualizzato un messaggio di accesso sull'applicazione, al completamento della pagina di accesso non viene chiusa e viene invece visualizzata una pagina vuota (nero). È possibile chiudere la pagina vuota o spostarla per individuare l'applicazione sottostante. Questo può verificarsi ad esempio durante l'accesso durante la registrazione MDM dall'app Impostazioni. 

## <a name="provide-feedback-and-report-issues"></a>Inviare commenti e suggerimenti e segnalare problemi

Usare l' [App Hub di feedback in HoloLens o Windows 10 PC](give-us-feedback.md) per inviare commenti e suggerimenti e segnalare problemi. L'uso dell'hub feedback garantisce che tutte le informazioni di diagnostica necessarie siano incluse per aiutare i nostri tecnici a eseguire rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si vuole che l'hub feedback acceda alla cartella documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto per cuffie immersive (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Supporto di HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](install-the-tools.md)
* [Inviare commenti e suggerimenti](give-us-feedback.md)

