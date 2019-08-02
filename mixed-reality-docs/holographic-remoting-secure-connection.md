---
title: Stabilire una connessione sicura con la comunicazione remota olografica
description: Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718075"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Stabilire una connessione sicura con la comunicazione remota olografica

>[!IMPORTANT]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.

Quando si esegue lo streaming di contenuto in HoloLens 2 su una rete non sicura, ad esempio un Wi-Fi aperto o Internet, è consigliabile usare una connessione crittografata.

>[!IMPORTANT]
>È consigliabile prendere in considerazione anche quando si usa un Wi-Fi locale attendibile usando una connessione crittografata.

Per poter usare una connessione crittografata, sarà necessario implementare sia un [lettore personalizzato](holographic-remoting-create-player.md) che un' [app host personalizzata](holographic-remoting-create-host.md).

La crittografia viene eseguita tramite l'implementazione TLS delle piattaforme sottostanti.

## <a name="basics-of-an-encrypted-connection"></a>Nozioni di base su una connessione crittografata

Per consentire uno scambio di certificati, è necessario implementare gli oggetti seguenti.

>[!TIP]
>L'implementazione di interfacce WinRT può essere eseguita C++facilmente con/WinRT. Il capitolo [API autore C++con/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis) descrive in modo dettagliato questo aspetto.

>[!IMPORTANT]
>Il ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` contenuto del pacchetto NuGet contiene la documentazione dettagliata per l'API relativa alle connessioni protette.

1) Oggetto Certificate, che deve implementare l' ```ICertificate``` interfaccia.

    * Restituisce il contenuto binario del certificato PFX tramite il ```GetCertificatePfx``` metodo. Uguale al contenuto binario di un file con estensione pfx.
    * Restituisce il nome del soggetto del ```GetSubjectName```certificato tramite.
    * Restituire la password PFX tramite ```GetPfxPassword```. Restituisce una stringa vuota per un PFX non protetto.

2) Provider di certificati che implementa ```ICertificateProvider``` l'interfaccia che fornisce un certificato quando viene richiesto ```GetCertificate``` tramite il metodo.

3) Validator del certificato che implementa ```ICertificateValidator``` l'interfaccia. L'attività consiste nel verificare i certificati in ingresso.
    * Il ```PerformSystemValidation``` metodo deve restituire ```true``` quando la piattaforma sottostante deve convalidare la catena di certificati ```false``` in ingresso; in caso contrario,.
    * ```ValidateCertificate```viene chiamato dal contesto client per richiedere la convalida di un certificato. Questo metodo accetta la catena di certificati (con il primo certificato che è il certificato oggetto), il nome del server con cui viene stabilita la connessione e se deve essere forzato un controllo di revoca. Il risultato della convalida del sistema verrà fornito se è stata richiesta la convalida dal sistema sottostante. Per continuare l'elaborazione ```CertificateValidated``` con il risultato appropriato o ```Cancel``` per annullare la convalida, è necessario chiamare sull'oggetto ```ICertificateValidationCallback```passato.

Inoltre, per consentire lo scambio di un token protetto, è necessario implementare gli oggetti seguenti.

1) Un provider di autenticazione che ```IAuthenticationProvider``` implementa l'interfaccia. Il ```GetToken``` metodo viene chiamato dal contesto client per richiedere un token per l'autenticazione client. Per continuare ```TokenReceived``` a fornire il token di autenticazione e continuare il processo di connessione ```Cancel``` oppure per annullare il processo, è necessario chiamare sull'oggetto ```IAuthenticationProviderCallback```passato.
2) Ricevitore di autenticazione che implementa ```IAuthenticationReceiver``` l'interfaccia. La relativa attività consiste nel convalidare i token in ingresso.
    * Il ```GetRealm``` metodo deve restituire il nome dell'area di autenticazione.
    * Il ```ValidateToken``` metodo viene chiamato dal contesto di rete del server per richiedere la convalida di un token di autenticazione client. Per continuare, chiamare ```ValidationCompleted``` il completamento del segnale della convalida o ```Cancel``` rifiutare la connessione client. La connessione client verrà accettata o rifiutata in base al risultato della convalida ```ValidationCompleted```passato a. 

Una volta implementati ```ListenSecure``` questi oggetti, è necessario chiamare ```Listen``` anziché e ```ConnectSecure``` anziché ```Connect``` nel contesto remoto e nel contesto del lettore rispettivamente. ```ListenSecure```richiede un provider di certificati e un ricevitore ```Listen```di autenticazione aggiuntivi. ```ConnectSecure```richiede un provider di autenticazione e un validator ```Connect```del certificato aggiuntivi.

## <a name="see-also"></a>Vedere anche
* [Scrittura di un'app host di comunicazione remota olografica](holographic-remoting-create-host.md)
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per la comunicazione remota olografica](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)