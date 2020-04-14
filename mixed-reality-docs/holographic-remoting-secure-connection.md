---
title: Stabilire una connessione sicura con la comunicazione remota olografica
description: Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278229"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Stabilire una connessione sicura con la comunicazione remota olografica

>[!IMPORTANT]
>Queste linee guida sono specifiche per la comunicazione remota olografica in HoloLens 2.

Questa pagina illustra come stabilire una connessione crittografata protetta quando si usa la comunicazione remota olografica.

Quando si esegue lo streaming di contenuto in HoloLens 2 su una rete non sicura, ad esempio un Wi-Fi aperto o Internet, è consigliabile usare una connessione crittografata.

>[!IMPORTANT]
>È consigliabile prendere in considerazione anche quando si usa un Wi-Fi locale attendibile usando una connessione crittografata.

Per poter usare una connessione crittografata, sarà necessario implementare sia un [lettore personalizzato](holographic-remoting-create-player.md) che un' [app remota personalizzata](holographic-remoting-create-host.md).

La crittografia viene eseguita tramite l'implementazione TLS delle piattaforme sottostanti.

## <a name="basics-of-an-encrypted-connection"></a>Nozioni di base su una connessione crittografata

Per consentire uno scambio di certificati, è necessario implementare gli oggetti seguenti.

>[!TIP]
>L'implementazione di interfacce WinRT può essere eseguita C++facilmente con/WinRT. Il capitolo [API autore C++con/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) descrive in modo dettagliato questo aspetto.

>[!IMPORTANT]
>Il ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` nel pacchetto NuGet contiene la documentazione dettagliata per l'API relativa alle connessioni protette.

1) Oggetto Certificate, che deve implementare l'interfaccia ```ICertificate```.

    * Restituisce il contenuto binario del certificato PFX tramite il metodo ```GetCertificatePfx```. Uguale al contenuto binario di un file con estensione pfx.
    * Restituisce il nome del soggetto del certificato tramite ```GetSubjectName```.
    * Restituire la password PFX tramite ```GetPfxPassword```. Restituisce una stringa vuota per un PFX non protetto.

2) Provider di certificati che implementa l'interfaccia ```ICertificateProvider``` che fornisce un certificato quando viene richiesto tramite il metodo ```GetCertificate```.

3) Validator del certificato che implementa l'interfaccia ```ICertificateValidator```. L'attività consiste nel verificare i certificati in ingresso.
    * Il metodo ```PerformSystemValidation``` deve restituire ```true``` quando la piattaforma sottostante deve convalidare la catena di certificati in ingresso, ```false``` in caso contrario.
    * ```ValidateCertificate``` viene chiamato dal contesto client per richiedere la convalida di un certificato. Questo metodo accetta la catena di certificati (con il primo certificato che è il certificato oggetto), il nome del server con cui viene stabilita la connessione e se deve essere forzato un controllo di revoca. Il risultato della convalida del sistema verrà fornito se è stata richiesta la convalida dal sistema sottostante. Per continuare l'elaborazione di ```CertificateValidated``` con il risultato appropriato o ```Cancel``` annullare la convalida deve essere chiamata sul ```ICertificateValidationCallback```passato.

Inoltre, per consentire lo scambio di un token protetto, è necessario implementare gli oggetti seguenti.

1) Un provider di autenticazione che implementa l'interfaccia ```IAuthenticationProvider```. Il metodo ```GetToken``` viene chiamato dal contesto client per richiedere un token per l'autenticazione client. Per continuare ```TokenReceived``` per fornire il token di autenticazione e continuare il processo di connessione oppure ```Cancel``` annullare il processo deve essere chiamato sul ```IAuthenticationProviderCallback```passato.
2) Ricevitore di autenticazione che implementa l'interfaccia ```IAuthenticationReceiver```. La relativa attività consiste nel convalidare i token in ingresso.
    * Il metodo ```GetRealm``` deve restituire il nome dell'area di autenticazione.
    * Il metodo ```ValidateToken``` viene chiamato dal contesto di rete del server per richiedere la convalida di un token di autenticazione client. Per continuare, chiamare ```ValidationCompleted``` per segnalare il completamento della convalida o ```Cancel``` per rifiutare la connessione client. La connessione client verrà accettata o rifiutata in base al risultato della convalida passato a ```ValidationCompleted```. 

Una volta implementati questi oggetti ```ListenSecure``` necessario chiamare anziché ```Listen``` e ```ConnectSecure``` anziché ```Connect``` rispettivamente nel contesto remoto e nel contesto del lettore. ```ListenSecure``` richiede un provider di certificati e un ricevitore di autenticazione aggiuntivi su ```Listen```. ```ConnectSecure``` richiede un provider di autenticazione e un validator del certificato aggiuntivi su ```Connect```.

## <a name="see-also"></a>Vedi anche
* [Scrittura di un'app remota olografica remota](holographic-remoting-create-host.md)
* [Scrittura di un'app lettore di comunicazione remota olografica personalizzata](holographic-remoting-create-player.md)
* [Limitazioni e risoluzione dei problemi di comunicazione remota olografica](holographic-remoting-troubleshooting.md)
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
