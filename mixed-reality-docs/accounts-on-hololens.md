---
title: Account in HoloLens
description: Come configurare e gestire gli account utente su HoloLens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, utente, account, aad, ad FS, account microsoft, account del servizio gestito, le credenziali
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599832"
---
# <a name="accounts-on-hololens"></a>Account in HoloLens

Durante la configurazione iniziale di HoloLens, gli utenti devono accedere con l'account da usare nel dispositivo. Questo account può essere un account Microsoft consumer o un account aziendale che è stato configurato in Azure Active Directory (AAD) o Active Directory Federation Services (ADFS).

Accesso a questo account durante l'installazione crea un profilo utente nel dispositivo che l'utente può usare per accedere, e in cui tutte le app verranno archiviati i dati. Questo stesso account fornisce anche Single Sign-On per le app, ad esempio Microsoft Edge o Skype tramite le API di gestione di Account di Windows.

Inoltre, quando si accede a un'organizzazione o account aziendale nel dispositivo, può essere usato anche criteri di gestione dei dispositivi mobili (MDM), se configurate dall'amministratore IT.

Ogni volta che il dispositivo viene riavviato o esce dalla modalità standby, vengono utilizzate le credenziali per questo account per accedere di nuovo. Se l'opzione l'applicazione un accesso aggiuntivo esplicito è abilitata nelle impostazioni, all'utente verrà richiesto di digitare nuovamente le proprie credenziali. Ogni volta che il dispositivo si riavvia dopo la ricezione e l'applicazione di un aggiornamento del sistema operativo, un accesso aggiuntivo esplicito è necessario.

## <a name="multi-user-support"></a>Supporto multiutente

>[!NOTE]
>Supporto di più utenti richiede Commercial Suite, poiché si tratta di un [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) funzionalità.

Inizia con la [Windows 10 April 2018 Update](release-notes-april-2018.md), HoloLens supporta più utenti all'interno dello stesso tenant AAD. Per utilizzare questa opzione è necessario impostare il dispositivo inizialmente con un account che appartiene all'organizzazione. Successivamente, altri utenti dal tenant stesso sarà in grado di accedere al dispositivo dalla schermata di accesso o toccando il riquadro utente nel pannello del menu Start per disconnettere l'utente esistente. 

Le app installate nel dispositivo saranno disponibili per tutti gli altri utenti, ma ognuna avrà i propri dati dell'app e le preferenze. Rimozione di un'app lo rimuoverà anche tutti gli altri utenti però. 

È possibile rimuovere gli utenti dei dispositivi dal dispositivo per recuperare spazio passando a Impostazioni > account > ad altri utenti. Verranno anche rimossi tutti i dati degli altri utenti dell'app dal dispositivo. 

## <a name="linked-accounts"></a>Account collegati

All'interno di un account singolo dispositivo, gli utenti possono collegare le credenziali dell'account web aggiuntivi allo scopo di semplificare l'accesso all'interno delle App (ad esempio, di Store) oppure per combinare l'accesso alle risorse personali e aziendali, analogamente alla versione Desktop di Windows. Accesso a un altro account in questo modo non separa i dati dell'utente creati nel dispositivo, ad esempio immagini o download. Una volta un account è stato connesso a un dispositivo, è possono rendere le app usano di esso con l'autorizzazione per ridurre la necessità di accedere a ogni app singolarmente.

## <a name="using-single-sign-on-within-an-app"></a>Utilizza single sign-on all'interno di un'app

Lo sviluppatore di applicazioni, è possibile sfruttare i vantaggi di ottenere un'identità connessa su HoloLens con il [API di gestione di Account Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), esattamente come si farebbe con gli altri dispositivi Windows. Alcuni esempi di codice per queste API sono disponibili [qui](http://go.microsoft.com/fwlink/p/?LinkId=620621).

Fornire il consenso gli interrupt qualsiasi account che possono verificarsi, ad esempio utente richiedente per informazioni sull'account, quando l'app richiede un token di autenticazione è necessario gestire l'autenticazione a due fattori e così via.

Se l'app richiede un tipo di account specifico che non è stato collegato in precedenza, l'app può chiedere il sistema richiede all'utente di aggiungerne uno. Questo attiverà il riquadro Impostazioni account in cui deve essere avviato come finestra figlio modale dell'app. Per le app 2D, verrà eseguito il rendering di questa finestra direttamente tramite il centro della tua app e per le app Unity, viene visualizzata brevemente l'utente dall'app holographic in modo che sia possibile eseguire il rendering di questa finestra figlio. Personalizzare i comandi e le azioni su questo riquadro è descritta [qui](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Enterprise e altro tipo di autenticazione

Se l'app fa uso di altri tipi di autenticazione, ad esempio NTLM, Basic o Kerberos, è possibile usare [dell'interfaccia utente delle credenziali Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) per raccogliere, elaborare e archiviare le credenziali dell'utente. L'esperienza utente per la raccolta di queste credenziali è molto simile a altri cloud basato su account gli interrupt e verrà visualizzati come un'app figlio all'inizio l'app 2D o sospendere brevemente un'app Unity in modo da visualizzare l'interfaccia utente.

## <a name="deprecated-apis"></a>API deprecate

Una differenza per lo sviluppo su HoloLens dal Desktop è che [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API non è completamente supportato. Anche se restituirà che un token se l'account primario si trova in buona-permanente, interrompe, ad esempio quelli descritti in precedenza non verrà visualizzata alcuna interfaccia utente per l'utente e avrà esito negativo autenticare correttamente l'account.

