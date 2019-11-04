---
title: Account in HoloLens
description: Come configurare e gestire gli account utente in HoloLens.
author: tmlyon
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, User, account, AAD, ADFS, Microsoft account, MSA, Credentials
ms.openlocfilehash: 5579cf53948b8bdbd4b41973dde7b8fc70a5aa31
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437090"
---
# <a name="accounts-on-hololens"></a>Account in HoloLens

Durante la configurazione iniziale di HoloLens, è necessario che gli utenti accedano con l'account che vogliono usare sul dispositivo. Questo account può essere un account Microsoft utente o un account aziendale che è stato configurato in Azure Active Directory (AAD) o Active Directory Federation Services (ADFS).

L'accesso a questo account durante l'installazione crea un profilo utente sul dispositivo che l'utente può usare per l'accesso e su cui verranno archiviati i dati in tutte le app. Questo stesso account fornisce anche l'accesso Single Sign-on per app quali Edge o Skype tramite le API di gestione account di Windows.

Inoltre, quando si accede a un account aziendale o aziendale sul dispositivo, può anche applicare criteri di gestione dei dispositivi mobili (MDM), se configurati dall'amministratore IT.

Ogni volta che il dispositivo viene riavviato o riprende dalla modalità standby, le credenziali per questo account vengono usate per eseguire di nuovo l'accesso. Se l'opzione che impone l'accesso esplicito è abilitata nelle impostazioni, all'utente verrà richiesto di digitare di nuovo le credenziali. Ogni volta che il dispositivo viene riavviato dopo la ricezione e l'applicazione di un aggiornamento del sistema operativo, è necessario un accesso esplicito.

## <a name="multi-user-support"></a>Supporto per più utenti

>[!NOTE]
>Il supporto per più utenti richiede la suite commerciale, perché si tratta di una funzionalità [di Windows olografica per le aziende](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) .

A partire dall' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md), HoloLens supporta più utenti all'interno dello stesso tenant di AAD. Per usarlo, è necessario configurare inizialmente il dispositivo con un account appartenente all'organizzazione. Successivamente, altri utenti dello stesso tenant saranno in grado di accedere al dispositivo dalla schermata di accesso o toccando il riquadro utente nel pannello Start per disconnettersi dall'utente esistente. 

Le app installate nel dispositivo saranno disponibili per tutti gli altri utenti, ma ognuna avrà i dati e le preferenze dell'app. Se si rimuove un'app, questa verrà rimossa anche per tutti gli altri utenti. 

È possibile rimuovere gli utenti del dispositivo dal dispositivo per recuperare spazio passando a Impostazioni > account > altre persone. Vengono rimossi anche tutti i dati dell'app degli altri utenti dal dispositivo. 

## <a name="linked-accounts"></a>Account collegati

All'interno di un singolo account del dispositivo, gli utenti possono collegare altre credenziali di account Web allo scopo di semplificare l'accesso all'interno delle app (ad esempio lo Store) o combinare l'accesso a risorse personali e di lavoro, in modo analogo alla versione desktop di Windows. L'accesso a un account aggiuntivo in questo modo non separa i dati utente creati nel dispositivo, ad esempio immagini o download. Una volta che un account è stato connesso a un dispositivo, le app possono usarlo con le autorizzazioni necessarie per ridurre la necessità di accedere singolarmente a ogni app.

## <a name="using-single-sign-on-within-an-app"></a>Uso di Single Sign-On all'interno di un'app

Gli sviluppatori di app possono sfruttare i vantaggi offerti dall'uso di un'identità connessa in HoloLens con le [API di gestione account di Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), proprio come si farebbe per altri dispositivi Windows. Alcuni esempi di codice per queste API sono disponibili [qui](https://go.microsoft.com/fwlink/p/?LinkId=620621).

Eventuali interrupt di account che possono verificarsi, ad esempio la richiesta del consenso dell'utente per le informazioni sull'account, l'autenticazione a due fattori e così via, devono essere gestiti quando l'app richiede un token di autenticazione.

Se l'app richiede un tipo di conto specifico che non è stato collegato in precedenza, l'app può chiedere al sistema di richiedere all'utente di aggiungerne una. In questo modo, il riquadro Impostazioni account verrà avviato come un figlio modale dell'app. Per le app 2D, questa finestra eseguirà il rendering direttamente sul centro dell'app e per le app Unity, in modo da estrarre brevemente l'utente dall'app olografica per poter eseguire il rendering della finestra figlio. La personalizzazione dei comandi e delle azioni in questo riquadro è descritta di [seguito](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Enterprise e altri tipi di autenticazione

Se l'app usa altri tipi di autenticazione, ad esempio NTLM, Basic o Kerberos, è possibile usare l' [interfaccia utente delle credenziali di Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) per raccogliere, elaborare e archiviare le credenziali dell'utente. L'esperienza utente per la raccolta di queste credenziali è molto simile ad altri interrupt di account basati sul cloud e verrà visualizzata come un'app figlio sull'app 2D o per sospendere brevemente un'app Unity per visualizzare l'interfaccia utente.

## <a name="deprecated-apis"></a>API deprecate

Una differenza per lo sviluppo su HoloLens dal desktop è che l'API [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) non è completamente supportata. Sebbene restituisca un token se l'account primario è in esecuzione, gli interrupt come quelli descritti in precedenza non visualizzeranno alcuna interfaccia utente per l'utente e non riusciranno a autenticare correttamente l'account.

