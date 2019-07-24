---
title: Note sulla versione-2016 agosto
description: Note sulla versione di HoloLens per la versione anniversario di Windows 10 (2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, note sulla versione, sistema operativo, piattaforma, funzionalità, suite commerciale
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524298"
---
# <a name="release-notes---august-2016"></a>Note sulla versione-2016 agosto

Il team di HoloLens è in attesa di commenti e suggerimenti da parte degli sviluppatori del programma Windows Insider per definire le priorità del lavoro. Continua a [inviare commenti e suggerimenti](give-us-feedback.md) tramite l'hub per i commenti, i [forum per sviluppatori](https://forums.hololens.com) e il [Twitter tramite @HoloLens ](https://twitter.com/hololens). Poiché Windows 10 abbraccia l'aggiornamento dell'anniversario, il team di HoloLens è lieto di offrire un ulteriore miglioramento dell'esperienza olografica. In questo aggiornamento abbiamo dedicato alle principali correzioni, miglioramenti e introduzione alle funzionalità richieste dalle aziende e disponibili in Microsoft HoloLens Commercial Suite.

**Ultima versione:** Aggiornamento di Windows olografico 2016 (**10.0.14393.0**, versione anniversario di Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Per eseguire l' [aggiornamento alla versione corrente](updating-hololens.md), aprire l'app *Impostazioni* , passare a *Aggiorna & sicurezza*, quindi selezionare il pulsante *Controlla aggiornamenti* .

## <a name="new-features"></a>Nuove funzionalità

**Connetti a processo di debug** HoloLens supporta ora il debug da Connetti a processo. È possibile usare Visual Studio 2015 Update 3 per connettersi a un'app in esecuzione in un HoloLens e avviarne il [debug](using-visual-studio.md#debugging-an-installed-or-running-app). Questa operazione funziona senza la necessità di eseguire la distribuzione da un progetto di Visual Studio.

**Aggiornamento** dell'emulatore di HoloLens È stata rilasciata anche una versione aggiornata dell'emulatore di HoloLens.

**Supporto di gamepad** È ora possibile associare e usare gamepad Bluetooth con HoloLens. Le funzionalità Bluetooth del controller wireless appena rilasciate e possono essere usate per riprodurre app e giochi abilitati per gamepad preferiti. Prima di poter connettere il controller senza fili Xbox a HoloLens, è necessario applicare un [aggiornamento del controller](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) . Il controller wireless Xbox S è supportato dalle API [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) e [Windows. Gaming. input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) . È possibile accedere a modelli aggiuntivi di controller Bluetooth tramite l'API [Windows. Gaming. input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) .

## <a name="improvements-and-fixes"></a>Miglioramenti e correzioni

Ci siamo sincronizzati con il resto dell'aggiornamento dell'anniversario di Windows 10, quindi, oltre a correzioni specifiche di Hololens, ricevi tutti i vantaggi di Windows Update per aumentare l'affidabilità e le prestazioni della piattaforma. I commenti e i suggerimenti sono altamente valutati e classificati in ordine di priorità per le correzioni della versione.

Sono state migliorate le esperienze seguenti:
* Accedi all'esperienza.
* aggiunta all'area di lavoro.
* efficienza energetica per le transizioni di stato dell'alimentazione del dispositivo.
* stabilità con acquisizioni di realtà miste.
* affidabilità per la connettività Bluetooth
* persistenza ologramma nello scenario con più app.

Sono stati corretti i problemi seguenti:
* non è possibile connettere i profiler e il debugger della grafica di Visual Studio.
* le foto & documenti non vengono visualizzati in Esplora file nel portale del dispositivo.
* la barra dell'app può lampeggiare quando il cursore viene posizionato sopra di esso in modalità di regolazione.
* Quando si usa la modalità di regolazione, il cursore a forma di occhio si passa al cursore a 4 frecce in un momento più lento.
* "Hey Cortana Play Music" non avvia Groove.
* dopo l'aggiornamento precedente, se si dice "Vai a casa", il pannello pin non viene visualizzato correttamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introduzione a Microsoft HoloLens Commercial Suite

Microsoft HoloLens Commercial Suite è pronto per la distribuzione aziendale. Sono state aggiunte diverse [funzionalità commerciali](commercial-features.md) altamente richieste dai partner commerciali iniziali.

Per acquistare Microsoft HoloLens Commercial Suite, contattare il responsabile del account Microsoft locale.

### <a name="key-commercial-features"></a>Caratteristiche commerciali principali 

* **Modalità tutto schermo.** Con la modalità tutto schermo HoloLens, è possibile limitare le app da eseguire per abilitare le esperienze demo o Showcase.<br>
  ![Con la modalità tutto schermo, HoloLens viene avviato direttamente nell'app che preferisci.](images/201608-kioskmode-400px.png)
* **Gestione di dispositivi mobili (MDM) per HoloLens.** Il reparto IT può gestire più dispositivi HoloLens contemporaneamente usando soluzioni come Microsoft Intune. Sarà possibile gestire le impostazioni, selezionare le app da installare e impostare le configurazioni di sicurezza personalizzate in base alle esigenze dell'organizzazione.<br>
  ![La gestione dei dispositivi mobili in HoloLens offre la gestione dei dispositivi di livello aziendale tra più dispositivi.](images/201608-enterprisemanagement-400px.png)
* **Windows Update per le aziende.** Aggiornamenti del sistema operativo controllati ai dispositivi e supporto per il ramo di manutenzione a lungo termine.
* **Sicurezza dei dati.** La crittografia dei dati BitLocker è abilitata in HoloLens per fornire lo stesso livello di protezione di qualsiasi altro dispositivo Windows.
* **Accesso al lavoro.** Tutti gli utenti dell'organizzazione possono connettersi in remoto alla rete aziendale tramite la rete privata virtuale in una HoloLens. HoloLens può accedere anche alle reti Wi-Fi che richiedono le credenziali.
* **Microsoft Store per le aziende.** Il reparto IT può anche configurare un archivio privato aziendale, contenente solo le app aziendali per l'utilizzo specifico di HoloLens. Distribuisci in modo sicuro il software aziendale a un gruppo selezionato di utenti aziendali.

### <a name="development-edition-vs-commercial-suite"></a>Confronto tra edizione di sviluppo e Suite commerciale

<table>
<tr>
<th>Funzionalità</th><th>Edizione di sviluppo</th><th>Suite commerciale</th>
</tr><tr>
<td>Crittografia del dispositivo (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rete privata virtuale (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modalità tutto schermo</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Gestione e distribuzione</th>
</tr><tr>
<td>Gestione di dispositivi mobili</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Possibilità di bloccare l'annullamento della registrazione</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Accesso Wi-Fi aziendale basato su certificati</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumer)</td><td style="text-align: center;">Consumatore</td><td style="text-align: center;">Filtraggio tramite MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portale di business Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicurezza e identità</th>
</tr><tr>
<td>Accedi con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Accedi con l'account Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenziali di nuova generazione con sblocco PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Avvio protetto</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Assistenza e supporto</th>
</tr><tr>
<td>Aggiornamenti automatici del sistema man mano che arrivano</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update per le aziende</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Ramo di manutenzione a lungo termine</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Problemi noti di HoloLens](hololens-known-issues.md)
* [Funzionalità commerciali](commercial-features.md)
* [Installare gli strumenti](install-the-tools.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
