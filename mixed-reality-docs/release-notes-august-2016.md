---
title: Note sulla versione - agosto 2016
description: HoloLens note sulla versione di Windows 10 Anniversary Release (autunno 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, release notes, sistema operativo, piattaforma, funzionalità, commercial suite
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603667"
---
# <a name="release-notes---august-2016"></a>Note sulla versione - agosto 2016

Il team di HoloLens è in ascolto per commenti e suggerimenti da parte degli sviluppatori nel programma Windows Insider per classificare il lavoro. Continuare a [commenti e suggerimenti](give-us-feedback.md) tramite l'Hub di commenti e suggerimenti, il [forum per sviluppatori](https://forums.hololens.com) e [Twitter tramite @HoloLens ](https://twitter.com/hololens). Come Windows 10 abbraccia che l'aggiornamento dell'anniversario, il team di HoloLens è lieta di offrire migliorano ulteriormente l'esperienza olografica. In questo aggiornamento, ci siamo concentrati sulle correzioni principali, miglioramenti e introduzione alle funzionalità richieste dalle aziende e disponibile in Microsoft HoloLens Commercial Suite.

**Versione più recente:** Aggiornamento di Windows Holographic agosto 2016 (**10.0.14393.0**, versione anniversario di Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Per [aggiornamento alla versione corrente](updating-hololens.md), aprire il *impostazioni* app, passare a *aggiornamento e sicurezza*, quindi selezionare il *Controlla aggiornamenti* pulsante.

## <a name="new-features"></a>Nuove funzionalità

**Collegare al debug di processi** HoloLens supporta adesso il debug Connetti a processo. È possibile usare Visual Studio 2015 Update 3 per connettersi a un'app in esecuzione su un HoloLens e [avviarne il debug](using-visual-studio.md#debugging-an-installed-or-running-app). Questa opzione funziona senza la necessità di eseguire la distribuzione da un progetto di Visual Studio.

**HoloLens Emulator aggiornato** sono state rilasciate anche una versione aggiornata dell'emulatore di HoloLens.

**Il supporto su gamepad** è ora possibile associare e usare gamepad Bluetooth con HoloLens. L'appena rilasciata Xbox Wireless Controller features capacità Bluetooth e può essere utilizzato per riprodurre le App e giochi preferiti su gamepad abilitata. Oggetto [aggiornamento del controller](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) devono essere applicati prima di poter connettere i dispositivi di Controller Xbox Wireless con HoloLens. Il Controller-S Wireless Xbox è supportata dal [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) e [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API. Modelli aggiuntivi dei controller Bluetooth sono accessibili tramite il [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>Miglioramenti e correzioni

Si sono sincronizzati con il resto dell'aggiornamento dell'anniversario di Windows 10, in modo che oltre alle correzioni specifiche Hololens, hai anche ricevuto tutti i tutti i vantaggi rispetto all'aggiornamento di Windows per migliorare le prestazioni e affidabilità della piattaforma. Commenti e suggerimenti sono estremamente con valori e la priorità per gli aggiornamenti nella versione.

Sono state migliorate le esperienze seguenti:
* log nelle esperienze.
* aggiunta alla rete.
* risparmio energetico per le transizioni di stato di potenza di dispositivo.
* maggiore stabilità con realtà mista consente di acquisire.
* affidabilità per la connettività Bluetooth
* persistenza di ologramma in uno scenario di app con più.

Sono stati corretti i problemi seguenti:
* il profiler di Visual Studio e debugger grafica non riuscire a connettersi.
* foto e documenti non vengono visualizzati in Esplora file nel portale di dispositivo.
* Barra dell'App può lampeggia quando il cursore viene posizionato sopra di esso in modalità di regolazione.
* In modalità di regolazione, l'occhio sguardo punto cursore cambierà aspetto per il cursore a freccia di 4 corrisponde a uno più lentamente.
* "Ehi Cortana Riproduci musica" non viene avviata Groove.
* Dopo l'aggiornamento precedente, che indica che "Go Home" non vengono visualizzati il pannello PIN correttamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introduzione a Microsoft HoloLens Commercial Suite

Microsoft HoloLens Commercial Suite è pronta per la distribuzione aziendale. Sono stati aggiunti molti più richiesti [le funzionalità commerciali](commercial-features.md) dai nostri partner di business anticipata.

Contattare l'account manager Microsoft locale per acquistare Commercial Suite Microsoft HoloLens.

### <a name="key-commercial-features"></a>Funzionalità commerciali principali 

* **Modalità tutto schermo.** Con la modalità tutto schermo HoloLens, è possibile limitare le app da eseguire per abilitare esperienze di demo o una presentazione.<br>
  ![Con la modalità per chiosco multimediale, HoloLens avvia direttamente nell'app di propria scelta.](images/201608-kioskmode-400px.png)
* **Gestione dei dispositivi mobili (MDM) per HoloLens.** Il reparto IT può gestire più dispositivi HoloLens contemporaneamente usando soluzioni quali Microsoft Intune. Sarà possibile gestire le impostazioni, selezionare le app da installare e impostare le configurazioni di sicurezza personalizzate in base alle esigenze dell'organizzazione.<br>
  ![Gestione dei dispositivi mobili su HoloLens fornisce gestione dei dispositivi di livello aziendale su più dispositivi.](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business.** Controllare gli aggiornamenti del sistema operativo per i dispositivi e il supporto per ramo di manutenzione a lungo termine.
* **Sicurezza dei dati.** La crittografia dei dati BitLocker è abilitata nel HoloLens per fornire lo stesso livello di protezione come qualsiasi altro dispositivo di Windows.
* **Accesso società.** Chiunque nell'organizzazione possa connettersi in remoto alla rete aziendale tramite rete privata virtuale in un HoloLens. HoloLens è possibile accedere anche le reti Wi-Fi che richiedono credenziali.
* **Microsoft Store per le aziende.** Il reparto IT può anche configurare un archivio privato dell'organizzazione, contenente solo le app aziendali per l'utilizzo di HoloLens specifico. Distribuire in modo sicuro un software enterprise per il gruppo selezionato di utenti aziendali.

### <a name="development-edition-vs-commercial-suite"></a>Edizione di sviluppo Visual Studio. Commercial Suite

<table>
<tr>
<th>Funzionalità</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>Crittografia del dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rete privata virtuale (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modalità tutto schermo</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Distribuzione e gestione</th>
</tr><tr>
<td>Gestione di dispositivi mobili</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Possibilità di bloccare l'annullamento della registrazione</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>L'accesso Wi-Fi aziendale basato su certificato</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Consumer)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Il filtro tramite MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portale Business Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicurezza e identità</th>
</tr><tr>
<td>Account di accesso con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Account di accesso con Account Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Le credenziali di generazione successiva con PIN sblocco</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Avvio protetto</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Per la manutenzione e supporto</th>
</tr><tr>
<td>Gli aggiornamenti automatici del sistema man mano che arrivano</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
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
