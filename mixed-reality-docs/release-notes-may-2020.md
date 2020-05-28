---
title: Note sulla versione-2020 maggio
description: Note sulla versione della realtà mista di Windows per Windows 10 2020 aggiornamento (noto anche come 2004).
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: Note sulla versione, versione, Windows 10, Build, 20H1, sistema operativo, maggio 2020, 2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124138"
---
# <a name="release-notes---may-2020"></a>Note sulla versione-2020 maggio

**Windows 10 May 2020 Update (v2004)** include nuove funzionalità per le cuffie per la realtà mista di Windows (VR), ad esempio la possibilità di avviare applicazioni Win32 nella Home realtà mista. HoloLens (1a generazione) è in manutenzione a lungo termine, con aggiornamenti di manutenzione da rilasciare mensilmente.

Per eseguire l'aggiornamento alla versione più recente sul PC per gli auricolari per la realtà mista di Windows (VR), aprire l'app **Impostazioni** , passare a **Aggiorna & sicurezza**, quindi selezionare il pulsante **Verifica aggiornamenti** . In un PC Windows 10, è anche possibile installare manualmente l' **aggiornamento di Windows 10 May 2020** usando lo [strumento di creazione di Windows Media](https://www.microsoft.com/software-download/windows10).

**Versione più recente per desktop**: Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Aggiornamenti per gli auricolari immersivi a realtà mista di Windows

### <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge
Come [annunciato in precedenza](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), sono stati apportati aggiornamenti per un supporto migliore con il nuovo browser Microsoft Edge in realtà mista di Windows. Il nuovo Microsoft Edge adotta il progetto Chromium open source per creare una migliore compatibilità Web per i clienti e meno frammentazione del Web per tutti gli sviluppatori Web. Supporta anche WebXR, il nuovo standard per la creazione di esperienze Web Immersive per le cuffie VR, al posto di WebVR.

### <a name="improved-settings-for-wmr"></a>Impostazioni migliorate per WMR
Grazie ai commenti e suggerimenti, abbiamo aggiunto e chiarito le impostazioni nella pagina di visualizzazione dell'auricolare:

* **Qualità visiva della Home** : la modifica di queste impostazioni influiscono solo sull'ambiente di casa realtà mista (Cliff House e Skyloft):

* **Modificare il livello di dettaglio e la qualità degli effetti nella Home realtà mista** : in questo modo vengono modificati alcuni effetti sul rendering usati nella Home page. In particolare, la qualità visiva dei diversi materiali (legno, calcestruzzo e così via) verrà ridimensionata quando si modifica questa impostazione da bassa ad alta.

* **Modificare la risoluzione della finestra dell'app** : per impostazione predefinita, la maggior parte delle finestre 2D avviate nella Home page viene avviata con una risoluzione 720p. Sebbene sia possibile ridimensionarli manualmente orizzontalmente & verticalmente, è anche possibile scegliere di avviarli tutti a 1080p. In precedenza questa opzione era disponibile come opzione molto alta (beta) in qualità visiva. È stato suddiviso in modo appropriato come impostazione separata.

* **Opzioni di esperienza** : queste opzioni consentono di modificare l'esperienza di realtà mista per ridurre il carico sui sistemi in cui l'hardware potrebbe avere difficoltà a tenere il passo con un 90 fps senza restrizioni. È possibile scegliere di abilitare o disabilitare in modo esplicito queste impostazioni aggiuntive oppure scegliere Consenti a Windows di decidere e lasciare che l'euristica continui a decidere quando attivare e disattivare queste impostazioni.

* **Risoluzione** : se si dispone di una cuffia ad alta risoluzione come il reverbio di HP, è supportata l'esecuzione con la risoluzione nativa oppure con una risoluzione ridotta per motivi di prestazioni. Gli auricolari precedenti, come Samsung Odyssey ed Odyssey +, supportano solo una singola risoluzione, in modo da non poter modificare questa impostazione in tali auricolari.

* **Frequenza dei fotogrammi** : è ora possibile impostare manualmente la frequenza dei fotogrammi dello schermo della cuffia oppure continuare a consentire a Windows di usare l'euristica per determinare se 60 hz o 90 Hz sono più appropriati.

* **Taratura** : come prima, è possibile regolare il dpi (interpupillare distance) se supportato dall'auricolare.

* **Commutazione di input** : attivare o disattivare il comportamento di commutazione dello stato attivo (Win + Y) automatico (in base ai commenti del sensore di presenza) o manuale.

### <a name="new-cortana-app"></a>Nuova app Cortana
Questo aggiornamento a Windows include la versione più recente dell'app Cortana, che attualmente è solo in lingua inglese (Stati Uniti) e non supporta più alcuni comandi specifici della realtà mista, ad esempio "scattare un'immagine" e "scattare un video". Sarà comunque possibile usare la nuova Cortana per avviare le app e supportare anche nuovi comandi mirati per la produttività, ad esempio, "quando il prossimo incontro?" oppure "Invia un messaggio di posta elettronica a <name> che sto eseguendo tardi".

#### <a name="please-help-us-improve"></a>Aiutaci a migliorare!
Si cerca continuamente di migliorare la compatibilità.  Se le applicazioni Win32 classiche preferite non si comportano correttamente durante la realtà mista di Windows, inviare commenti e suggerimenti tramite l'hub per i [Commenti](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione-2019 maggio](release-notes-may-2019.md)
* [Note sulla versione - ottobre 2018](release-notes-october-2018.md)
* [Note sulla versione-2018 aprile](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto per cuffie immersive (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Supporto di HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](install-the-tools.md)
* [Invia commenti e suggerimenti](give-us-feedback.md)
