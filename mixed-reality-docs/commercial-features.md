---
title: Funzionalità commerciali
description: Microsoft HoloLens Commercial Suite include funzionalità che semplificano alle aziende di gestire i dispositivi HoloLens.
author: xerxesb85
ms.author: xerxesb
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, commerciali e le funzionalità mdm, gestione dei dispositivi mobili, la modalità tutto schermo
ms.openlocfilehash: 5fd5c56983fb3e94376fac08c6e96510bccc0002
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604990"
---
# <a name="commercial-features"></a>Funzionalità commerciali

Microsoft HoloLens Commercial Suite include funzionalità che semplificano alle aziende di gestire i dispositivi HoloLens. Le funzionalità commerciali sono inclusi nel sistema operativo Windows, ma sono abilitate da una licenza. In quasi tutti i casi, la licenza è abilitata per la gestione dei dispositivi Microsoft quando HoloLens viene registrato in un'organizzazione. Contattare l'account manager Microsoft locale per acquistare Commercial Suite Microsoft HoloLens.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## <a name="key-commercial-features"></a>Funzionalità commerciali principali

* **Modalità tutto schermo.** Con la modalità tutto schermo HoloLens, è possibile limitare le app da eseguire per abilitare esperienze di demo o una presentazione.

  ![Con la modalità per chiosco multimediale, HoloLens avvia direttamente nell'app di propria scelta.](images/201608-kioskmode-400px.png)

* **Gestione dei dispositivi mobili (MDM) per HoloLens.** Il reparto IT può gestire più dispositivi HoloLens contemporaneamente usando soluzioni quali Microsoft Intune. Sarà possibile gestire le impostazioni, selezionare le app da installare e impostare le configurazioni di sicurezza personalizzate in base alle esigenze dell'organizzazione.

  ![Gestione dei dispositivi mobili su HoloLens fornisce gestione dei dispositivi di livello aziendale su più dispositivi.](images/201608-enterprisemanagement-400px.png)
  
* **Windows Update for Business.** Controllare gli aggiornamenti del sistema operativo per i dispositivi e il supporto per ramo di manutenzione a lungo termine.
* **Sicurezza dei dati.** La crittografia dei dati BitLocker è abilitata nel HoloLens per fornire lo stesso livello di protezione come qualsiasi altro dispositivo di Windows.
* **Accesso società.** Chiunque nell'organizzazione possa connettersi in remoto alla rete aziendale tramite rete privata virtuale in un HoloLens. HoloLens è possibile accedere anche le reti Wi-Fi che richiedono credenziali.
* **Microsoft Store per le aziende.** Il reparto IT può anche configurare un archivio privato dell'organizzazione, contenente solo le app aziendali per l'utilizzo di HoloLens specifico. Distribuire in modo sicuro un software enterprise per il gruppo selezionato di utenti aziendali.

## <a name="development-edition-vs-commercial-suite"></a>Edizione di sviluppo Visual Studio. Commercial Suite

<table>
<tr>
<th>Funzionalità</th><th>HoloLens Development Edition</th><th>HoloLens Commercial Suite</th><th>HoloLens 2</th>
</tr><tr>
<td>Crittografia del dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rete privata virtuale (VPN)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modalità tutto schermo</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Distribuzione e gestione</th>
</tr><tr>
<td>Gestione di dispositivi mobili</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Possibilità di bloccare l'annullamento della registrazione</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>L'accesso Wi-Fi aziendale basato su certificato</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Consumer)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Il filtro tramite MDM</td><td style="text-align: center;">Il filtro tramite MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portale Business Store</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicurezza e identità</th>
</tr><tr>
<td>Account di accesso con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Account di accesso con Account Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Le credenziali di generazione successiva con PIN sblocco</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Avvio protetto</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Per la manutenzione e supporto</th>
</tr><tr>
<td>Gli aggiornamenti automatici del sistema man mano che arrivano</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Ramo di manutenzione a lungo termine</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>



## <a name="enabling-commercial-features"></a>Abilitare le funzionalità commerciali

Le funzionalità commerciali come Microsoft Store per le aziende, la modalità per chiosco multimediale, e accesso Wi-Fi aziendale vengono configurati da un'organizzazione amministratore IT. Il [Windows IT Center per HoloLens](https://technet.microsoft.com/itpro/hololens/index) fornisce istruzioni dettagliate per la registrazione del dispositivo e l'installazione di App da Microsoft Store per le aziende.

## <a name="see-also"></a>Vedere anche
* [IT Pro Guide per HoloLens](https://technet.microsoft.com/itpro/hololens/index)
* [Modalità tutto schermo](using-the-windows-device-portal.md#kiosk-mode)
* [CSP supportati in Windows Holographic for enterprise](https://msdn.microsoft.com/library/windows/hardware/dn920025(v=vs.85).aspx#HoloLens)
* [Microsoft Store For Business e applicazioni line of business](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
* [Uso delle App line-of-business](https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps)
