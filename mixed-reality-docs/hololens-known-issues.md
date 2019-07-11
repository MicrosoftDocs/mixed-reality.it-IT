---
title: Problemi noti di HoloLens
description: Si tratta dell'elenco di problemi noti che possono interessare gli sviluppatori di HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: risolvere i problemi, problema noto, Guida
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789483"
---
# <a name="hololens-known-issues"></a>Problemi noti di HoloLens

Si tratta dell'elenco corrente dei problemi noti per gli sviluppatori che hanno effetto sui HoloLens. Vedere prima qui se si nota un comportamento strano. Questo elenco verrà mantenuto aggiornato quando vengono individuati o segnalati nuovi problemi o quando i problemi vengono risolti negli aggiornamenti futuri di software HoloLens.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Non è possibile connettere e distribuire in HoloLens tramite Visual Studio

>[!NOTE]
>Ultimo aggiornamento: 7 o 8 @ 7 alle 19:25 - il team ha identificato la causa radice e sta attualmente lavorando correzione. Soluzione alternativa è disponibile di seguito. 

È stato in grado di identificare la causa radice del problema. Gli utenti utilizzati nelle prime versioni di Visual Studio 2017 o Visual Studio 2015 per distribuire ed eseguire il debug delle applicazioni nella loro HoloLens e quindi successivamente le ultime versioni di Visual Studio 2017 o Visual Studio 2019 con la stessa HoloLens saranno interessati. 

Le versioni più recenti di Visual Studio distribuisce una nuova versione di un componente, ma sono rimasti file rispetto alla versione meno recente nel dispositivo, causando la versione più recente avere esito negativo.  In questo modo il messaggio di errore seguente: DEP0100: Assicurarsi che tale dispositivo di destinazione è abilitata la modalità sviluppatore. Non è stato possibile ottenere una licenza per sviluppatori su <ip> a causa dell'errore 80004005.
 
**Soluzione temporanea**: 

Il team sta attualmente lavorando una correzione. Nel frattempo, è possibile utilizzare la procedura seguente per risolvere il problema e consentire distribuzione e debug di sblocco:  
1. Aprire Visual Studio
2. File -> Nuovo -> progetto
3. Visual C# -> Windows Desktop -> App Console (.NET Framework)
4. Assegnare un nome (ad esempio HoloLensDeploymentFix) al progetto e assicurarsi che il Framework è impostato su almeno .NET Framework 4.5, è possibile fare quindi clic su OK.
5. Fare doppio clic sul nodo Riferimenti in Esplora soluzioni e aggiungere i riferimenti seguenti (fai clic per la sezione 'Sfoglia' e fare clic su 'Sfoglia' pulsante):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Se non hai 10.0.18362.0 installato, usare la versione più recente che è necessario.
 
6. Pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Aggiungi -> elemento esistente.
 
7. Passare a C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 e modificare il filtro "tutti i file (\*.\*)"
 
8. Selezionare sia SirepClient.dll SshClient.dll e fare clic su "Aggiungi".
 
9. Individuare e selezionare entrambi i file in Esplora soluzioni (devono essere nella parte inferiore dell'elenco di file) e modificare "Copia nella Directory di Output" nella finestra proprietà su "Copia sempre"
 
10. Nella parte superiore del file, aggiungere quanto segue per un elenco di istruzioni 'using' esistente: 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. All'interno di "static void Main(...)", aggiungere il codice seguente:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Compila -> Compila soluzione
 
13. Aprire un prompt dei comandi nella cartella che contiene il .exe compilati (ad esempio C:\MyProjects\HoloLensDeploymentFix\bin\Debug)
 
14. Eseguire il file eseguibile e specificare l'indirizzo IP del dispositivo come un argomento della riga di comando.  (Se è connesso tramite USB, è possibile usare 127.0.0.1, in caso contrario, usare l'indirizzo IP WiFi del dispositivo.)  Ad esempio, "HoloLensDeploymentFix 127.0.0.1"
 
15. Una volta lo strumento è stato terminato senza visualizzare alcun messaggio (l'operazione dovrebbe richiedere solo alcuni secondi), sarà ora in grado di distribuire ed eseguire il debug da Visual Studio 2017 o versione successiva.  Poter continuare a utilizzare lo strumento non è necessario.

Verranno forniti ulteriori aggiornamenti man mano che diventano disponibili.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemi di avvio di Microsoft Store e App in HoloLens

>[!NOTE]
>Ultimo aggiornamento: 4/2 AM 10 - risoluzione del problema. 

Si potrebbero riscontrare problemi durante il tentativo di avviare l'App in HoloLens e Microsoft Store. È stato determinato che il problema si verifica quando gli aggiornamenti delle app in background distribuire una versione più recente dei pacchetti di framework di sequenze specifiche mentre uno o più delle proprie App dipendenti sono ancora in esecuzione. In questo caso, un aggiornamento automatici delle app recapitato una nuova versione di .NET Framework nativo (versione 10.0.25531 a 10.0.27413) ha causato l'App in esecuzione in modo non corretto aggiornamento per tutte le App in esecuzione, utilizzo la versione precedente di framework.  Il flusso per l'aggiornamento framework è come segue:-

1.  Viene scaricato dall'archivio e installato il nuovo pacchetto di framework
2.  Tutte le app usando il framework meno recente vengono 'aggiornate' per usare la versione più recente

Se il passaggio 2 viene interrotta prima del completamento, le App per cui non è stato registrato il framework più recente avrà esito negativo avviare dal menu start.  Crediamo che qualsiasi app in HoloLens potrebbero essere interessati da questo problema.

Alcuni utenti hanno segnalato che chiusura delle App bloccate e l'avvio di altre App, ad esempio Hub di commenti e suggerimenti, 3D visualizzatore o foto risolve il problema relativo a essi, tuttavia, questa soluzione non funziona 100% del tempo.

Abbiamo radice ha causato il problema non causata l'aggiornamento stesso, ma un bug nel sistema operativo che ha comportato l'aggiornamento di framework .NET Native viene gestito in modo non corretto. Siamo lieti di annunciare che abbiamo identificato una correzione e sia stato rilasciato un aggiornamento (versione 17763.380 del sistema operativo) che contiene la correzione. 

Per vedere se il dispositivo può richiedere l'aggiornamento.:

1.  Passare all'app "Impostazioni" e aprire "Aggiornamento e sicurezza"
2.  Fare clic su "Controlla aggiornamenti"
3.  Se è disponibile l'aggiornamento a 17763.380, aggiornarla a questa build per ricevere la correzione del bug di blocco App
4.  Al momento dell'aggiornamento a questa versione del sistema operativo, l'App dovrebbe funzionare come previsto.

Inoltre, come facciamo con ogni versione del sistema operativo HoloLens, al termine della registrazione dell'immagine FFU a Microsoft Download Center al https://aka.ms/hololensdownload/10.0.17763.380. 

Se non si vuole eseguire l'aggiornamento, Microsoft ha rilasciato una nuova versione dell'app UWP di Microsoft Store a partire da 3/29. Dopo aver ottenuto la versione aggiornata della Store:

1) Aprire la Store e confermare che viene caricato.
2) Usare il movimento Bloom per aprire il menu di scelta.
3) Tenta di aprire le app vengono interrotte in precedenza
3) Se ancora non può essere avviata, tenendo premuta l'icona dell'app interrotti e selezionare Disinstalla.
4) Resinstall queste App dallo store.

Se il dispositivo è ancora possibile caricare le app, puoi trasferirla in locale una versione di .NET Framework nativo e di Runtime tramite l'interfaccia di download in questo modo:

1)  È necessario scaricare [questo file zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) dal Microsoft Download Center.  Durante la decompressione produce due file.  Microsoft.NET.Native.Runtime.1.7.appx e Microsoft.NET.Native.Framework.1.7.appx
2)  Verificare che il dispositivo sia sbloccato dev.  Se non è stato fatto prima che le istruzioni per eseguire questa operazione siano [qui](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  Poi si desidera ottenere il Windows Device Portal.  Si consiglia di eseguire questa operazione tramite USB e si procede digitando http://127.0.0.1:10080 nel browser.  
4)  Dopo aver ottenuto il Windows Device Portal backup è necessario è "sideload" i due file di cui è stato scaricato.  Per farlo è necessario scendere barra laterale sinistra fino a quando non si ottengono la sezione "App" e fare clic su "App".
5)  Si verrà quindi visualizzata una schermata simile di sotto.  Si desidera passare alla sezione con la dicitura "Installare App" e passare a cui è stato decompresso questi due file APPX.  È possibile eseguire solo una alla volta, quindi, dopo aver selezionato il primo, quindi fare clic su "Vai" sotto la sezione "installazione".  Quindi eseguire questa operazione per il secondo file APPX. 
  ![Windows Device Portal per installare le app caricate in sideload](images/20190322-DevicePortal.png)<br>
6)  A questo punto siamo convinti che le applicazioni dovrebbe funzionare di nuovo e che è possibile anche ottenere la Store.
7)  In alcuni casi, è necessario eseguire il passaggio aggiuntivo di avviare l'app Visualizzatore 3D prima App interessate verranno avviate. 

Apprezziamo la pazienza dimostrata la procedura per risolvere questo problema è stato effettuato e saremo lieti di continuato a funzionare con la community di realtà mista riuscito di creare esperienze.

## <a name="connecting-to-wifi"></a>La connessione al Wi-Fi

Durante la configurazione guidata impostazioni, è un timeout di credenziale di 2 minuti. Il nome utente e la password deve essere immesso entro 2 minuti in caso contrario, che il campo nome utente verrà cancellato automaticamente.

È consigliabile usare una tastiera Bluetooth per l'immissione di password lunghe.

## <a name="device-update"></a>Aggiornamento del dispositivo
* 30 secondi dopo che un nuovo aggiornamento, la shell potrebbe scomparire una volta. Eseguire la **bloom** movimento per riprendere la sessione.

## <a name="visual-studio"></a>Visual Studio
* Visualizzare [installare gli strumenti](install-the-tools.md) per la versione più aggiornata di Visual Studio consigliato per lo sviluppo di HoloLens.
* Quando si distribuisce un'app da Visual Studio di HoloLens, si verifichi l'errore: **L'operazione richiesta non può essere eseguita su un file con un utente con mapping eseguito sezione aperta. (Eccezione da HRESULT: 0x800704C8)** . In questo caso, ripetere l'operazione e la distribuzione in genere avranno esito positivo.

## <a name="emulator"></a>Emulatore
* Non tutte le app di Microsoft Store sono compatibili con l'emulatore. Ad esempio, Conker Young e i frammenti non sono riproducibili nell'emulatore.
* È possibile usare la webcam PC nell'emulatore.
* La funzionalità di anteprima in tempo reale di Windows Device Portal non funziona con l'emulatore. È comunque possibile acquisire le immagini e video di realtà mista.

## <a name="unity"></a>Unity
* Visualizzare [installare gli strumenti](install-the-tools.md) per la versione più aggiornata di Unity consigliato per lo sviluppo di HoloLens.
* Problemi noti relativi a Unity HoloLens Technical Preview sono documentati nel [forum di HoloLens Unity](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* La funzionalità di anteprima in tempo reale nell'acquisizione di realtà mista può presentare molti secondi di latenza.
* Nella pagina Input virtuale, i controlli di movimento e scorrere verso la sezione movimenti virtuale non sono funzionali. Usarle avrà alcun effetto. La tastiera virtuale nella stessa pagina funziona correttamente.
* Dopo aver abilitato la modalità di sviluppo in impostazioni, potrebbe richiedere alcuni secondi prima di abilitata l'opzione per attivare il portale del dispositivo.

## <a name="api"></a>API
* Se l'applicazione imposta il [concentrarsi punto](focus-point-in-unity.md) dietro l'utente o il normale a camera.forward, vntana non compariranno nella realtà mista acquisire foto o video. Fino a quando questo bug è stato risolto in Windows, se le applicazioni impostare attivamente il [concentrarsi punto](focus-point-in-unity.md) dovrà garantire di piano normale è impostato opposto fotocamera feedforward (ad esempio, normale = - camera.forward).

## <a name="xbox-wireless-controller"></a>Controller Xbox Wireless
* Controller Xbox Wireless-S deve essere aggiornato prima di poter essere utilizzato con HoloLens. Verificare che siano [aggiornati](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) prima di tentare di associare il controller con un HoloLens.
* Se si riavvia il HoloLens mentre il Controller di Xbox Wireless è connesso, il controller non verrà riconnessa automaticamente a HoloLens. Alla luce di pulsante Guida lampeggerà lentamente finché le potenze di controller disattivato dopo 3 minuti. Per riconnettersi immediatamente, il controller di spegnere il controller tenendo premuto il pulsante Guida fino a quando non disattiva la luce. Quando si accende il controller anche in questo caso, riconnetterà a HoloLens.
* Se il HoloLens entra in modalità standby mentre è connesso il Controller Wireless Xbox, qualsiasi input nel controller di riattivazione di HoloLens. È possibile impedire questo comportamento lo spegnimento del controller, dopo aver utilizzarlo.
