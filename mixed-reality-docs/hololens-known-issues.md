---
title: Problemi noti di HoloLens
description: Questo è l'elenco dei problemi noti che possono influire sugli sviluppatori di HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: risoluzione dei problemi, problema noto, guida
ms.openlocfilehash: 80bd7499c0075399e516648dd92b7515fdba753a
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122127"
---
# <a name="hololens-known-issues"></a>Problemi noti di HoloLens

Si tratta dell'elenco corrente di problemi noti relativi a HoloLens che interessano gli sviluppatori. Controllare prima di tutto se viene visualizzato un comportamento strano. Questo elenco verrà mantenuto aggiornato quando vengono rilevati o segnalati nuovi problemi o quando si verificano problemi negli aggiornamenti software HoloLens futuri.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Non è possibile connettersi e distribuire in HoloLens tramite Visual Studio

>[!NOTE]
>Ultimo aggiornamento: 8/8 @ 5:23.00-Visual Studio ha rilasciato VS 2019 versione 16,2, che include una correzione per questo problema. Per evitare di riscontrare questo errore, è consigliabile eseguire l'aggiornamento alla versione più recente.

Visual Studio ha rilasciato VS 2019 versione 16,2, che include una correzione per questo problema. Per evitare di riscontrare questo errore, è consigliabile eseguire l'aggiornamento alla versione più recente.

Causa radice del problema: Gli utenti che hanno usato Visual Studio 2015 o le versioni precedenti di Visual Studio 2017 per distribuire ed eseguire il debug delle applicazioni nella HoloLens e successivamente hanno usato le versioni più recenti di Visual Studio 2017 o Visual Studio 2019 con lo stesso HoloLens saranno interessati. Le versioni più recenti di Visual Studio distribuiscono una nuova versione di un componente, ma i file della versione precedente vengono lasciati nel dispositivo, causando la mancata riuscita della versione più recente.  Viene generato il messaggio di errore seguente: DEP0100: Assicurarsi che la modalità sviluppatore del dispositivo di destinazione sia abilitata. Non è stato possibile ottenere una licenza <ip> per sviluppatori a causa dell'errore 80004005.
 
**Soluzione temporanea**: 

Anche se questo problema è stato risolto in Visual Studio 2019 16,2, gli sviluppatori che scelgono di rimanere nelle versioni precedenti di Visual Studio possono usare i passaggi seguenti per risolvere il problema e contribuire a sbloccare la distribuzione e il debug:  
1. Aprire Visual Studio
2. Nuovo progetto > di > file
3. Visual C# -> Windows Desktop-App console > (.NET Framework)
4. Assegnare un nome al progetto (ad esempio HoloLensDeploymentFix) e verificare che il Framework sia impostato su almeno .NET Framework 4,5 e quindi fare clic su OK.
5. Fare clic con il pulsante destro del mouse sul nodo riferimenti in Esplora soluzioni e aggiungere i riferimenti seguenti. fare clic sulla sezione "Sfoglia" e fare clic su "Sfoglia". pulsante):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Se 10.0.18362.0 non è installato, usare la versione più recente.
 
6. Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Aggiungi > elemento esistente.
 
7. Passare a C:\Programmi (x86) \Windows Kits\10\bin\10.0.18362.0\x86 e impostare il filtro su "tutti i file\*(\*.)"
 
8. Selezionare SirepClient. dll e SshClient. dll e fare clic su "Aggiungi".
 
9. Individuare e selezionare entrambi i file in Esplora soluzioni (devono trovarsi nella parte inferiore dell'elenco di file) e modificare "copia nella directory di output" nel Finestra Proprietà a "copia sempre"
 
10. All'inizio del file aggiungere il codice seguente all'elenco esistente di istruzioni ' using ': 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. All'interno di "static void Main (...)" aggiungere il codice seguente:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Compilazione-> soluzione di compilazione
 
13. Aprire un prompt dei comandi nella cartella che contiene il file con estensione exe compilato, ad esempio C:\MyProjects\HoloLensDeploymentFix\bin\Debug
 
14. Eseguire il file eseguibile e specificare l'indirizzo IP del dispositivo come argomento della riga di comando.  Se si è connessi tramite USB, è possibile usare 127.0.0.1, altrimenti usare l'indirizzo IP Wi-Fi del dispositivo.  Ad esempio, "HoloLensDeploymentFix 127.0.0.1"
 
15. Una volta che lo strumento è stato terminato senza messaggi (l'operazione dovrebbe richiedere solo alcuni secondi), ora sarà possibile distribuire ed eseguire il debug da Visual Studio 2017 o versione successiva.  L'uso continuo dello strumento non è necessario.


## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemi di avvio del Microsoft Store e delle app in HoloLens

>[!NOTE]
>Ultimo aggiornamento: 4/2 @ 10 AM-problema risolto. 

È possibile che si verifichino problemi durante il tentativo di avviare il Microsoft Store e le app in HoloLens. È stato determinato che il problema si verifica quando gli aggiornamenti delle app in background distribuiscono una versione più recente dei pacchetti del Framework in sequenze specifiche mentre una o più app dipendenti sono ancora in esecuzione. In questo caso, un aggiornamento automatico delle app ha fornito una nuova versione del Framework .NET Native (versione 10.0.25531 a 10.0.27413) ha causato l'aggiornamento delle app che eseguono non correttamente per tutte le applicazioni in esecuzione che utilizzano la versione precedente del Framework.  Il flusso per l'aggiornamento del Framework è il seguente:-

1.  Il nuovo pacchetto del Framework viene scaricato dall'archivio e installato
2.  Tutte le app che usano il Framework precedente sono ' aggiornate ' per usare la versione più recente

Se il passaggio 2 viene interrotto prima del completamento, le app per cui il Framework più recente non è stato registrato non verranno avviate dal menu Start.  Si ritiene che qualsiasi app in HoloLens possa essere interessata da questo problema.

Alcuni utenti hanno segnalato che la chiusura di app bloccate e l'avvio di altre app come l'hub di feedback, il visualizzatore 3D o le foto risolve il problema per loro. Tuttavia, questo non funziona il 100% del tempo.

La radice ha causato il fatto che questo problema non è stato causato dall'aggiornamento, ma un bug nel sistema operativo che ha comportato l'aggiornamento di .NET Native Framework non è stato gestito correttamente. Siamo lieti di annunciare che è stata identificata una correzione e che è stato rilasciato un aggiornamento (versione del sistema operativo 17763,380) che contiene la correzione. 

Per verificare se il dispositivo può eseguire l'aggiornamento, eseguire le operazioni seguenti:

1.  Passare all'app "Settings" e aprire "Update & Security".
2.  Fare clic su "Verifica disponibilità aggiornamenti"
3.  Se è disponibile l'aggiornamento a 17763,380, eseguire l'aggiornamento a questa compilazione per ricevere la correzione per il bug di blocco dell'app
4.  Dopo l'aggiornamento a questa versione del sistema operativo, le app dovrebbero funzionare come previsto.

Inoltre, come per ogni versione del sistema operativo HoloLens, l'immagine FFU è stata pubblicata nell'area download Microsoft all'indirizzo https://aka.ms/hololensdownload/10.0.17763.380. 

Se non si vuole eseguire l'aggiornamento, è stata rilasciata una nuova versione dell'app Microsoft Store UWP a partire da 3/29. Quando si dispone della versione aggiornata dello Store:

1) Aprire l'archivio e verificare che venga caricato.
2) Usare il movimento Bloom per aprire il menu.
3) Tentativo di aprire le app precedentemente interrotte
3) Se non è ancora possibile avviarlo, toccare e tenere premuto l'icona dell'app interruppe e selezionare Disinstalla.
4) Resinstall le app dallo Store.

Se il dispositivo non è ancora in grado di caricare le app, è possibile sideload una versione di .NET Native Framework e il runtime tramite l'area download eseguendo le operazioni seguenti:

1)  Scaricare [questo file zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) dall'area download Microsoft.  La decompressione produrrà due file.  Microsoft. NET. native. Runtime. 1.7. appx e Microsoft. NET. native. Framework. 1.7. appx
2)  Verificare che lo sviluppatore del dispositivo sia sbloccato.  Se questa operazione non è stata eseguita prima delle istruzioni, fare clic [qui](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  Si desidera quindi accedere al portale del dispositivo Windows.  Si consiglia di eseguire questa operazione su USB. questa operazione può essere eseguita digitando http://127.0.0.1:10080 nel browser.  
4)  Una volta installato il portale per dispositivi Windows, è necessario eseguire il caricamento laterale dei due file scaricati.  A tale scopo, è necessario scendere sulla barra laterale sinistra fino a visualizzare la sezione "app" e fare clic su "app".
5)  Verrà visualizzata una schermata simile alla seguente.  Si vuole passare alla sezione "Install app" e passare alla posizione in cui sono stati decompressi i due file APPX.  È possibile eseguire una sola operazione alla volta, quindi, dopo aver selezionato il primo, fare clic su "Vai" nella sezione Distribuisci.  Eseguire quindi questa operazione per il secondo file APPX. 
  ![Portale per dispositivi Windows per installare un'app con caricamento laterale](images/20190322-DevicePortal.png)<br>
6)  A questo punto, si ritiene che le applicazioni debbano iniziare a lavorare di nuovo e che sia possibile ottenere anche lo Store.
7)  In alcuni casi, è necessario eseguire il passaggio aggiuntivo dell'avvio dell'app visualizzatore 3D prima che le app interessate vengano avviate. 

Ci rendiamo conto della pazienza del processo di risoluzione di questo problema e ci auguriamo di continuare a collaborare con la nostra community per creare esperienze di realtà miste efficaci.

## <a name="connecting-to-wifi"></a>Connessione al Wi-Fi

Durante le impostazioni di & OOBE, il timeout delle credenziali è di 2 minuti. Il nome utente e la password devono essere immessi entro 2 minuti, altrimenti il campo nome utente verrà cancellato automaticamente.

Si consiglia di usare una tastiera Bluetooth per l'immissione di password lunghe.

>[!NOTE]
> Se durante la configurazione guidata viene selezionata la rete errata, il dispositivo dovrà essere reimpostato completamente. Le istruzioni sono disponibili [qui.](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery) 

## <a name="device-update"></a>Aggiornamento del dispositivo
* 30 secondi dopo un nuovo aggiornamento, la shell può scomparire una sola volta. Per riprendere la sessione, eseguire il movimento **Bloom** .

## <a name="visual-studio"></a>Visual Studio
* Vedere [installare gli strumenti](install-the-tools.md) per la versione più aggiornata di Visual Studio consigliata per lo sviluppo di HoloLens.
* Quando si distribuisce un'app da Visual Studio a HoloLens, è possibile che venga visualizzato l'errore: **Impossibile eseguire l'operazione richiesta su un file con una sezione mappata all'utente aperta. (Eccezione da HRESULT: 0x800704C8)** . In tal caso, riprovare e la distribuzione avrà in genere esito positivo.

## <a name="emulator"></a>Emulatore
* Non tutte le app nel Microsoft Store sono compatibili con l'emulatore. Ad esempio, i Conker e i frammenti giovani non sono riproducibili nell'emulatore.
* Non è possibile usare la webcam per PC nell'emulatore.
* La funzionalità di anteprima in tempo reale del portale per dispositivi Windows non funziona con l'emulatore. È ancora possibile acquisire immagini e video in realtà mista.

## <a name="unity"></a>Unity
* Vedere [installare gli strumenti](install-the-tools.md) per la versione più aggiornata di Unity consigliata per lo sviluppo di HoloLens.
* I problemi noti relativi a Unity HoloLens Technical Preview sono documentati nei [Forum di HoloLens Unity](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* La funzionalità di anteprima in tempo reale nell'acquisizione di realtà mista può presentare diversi secondi di latenza.
* Nella pagina input virtuali i controlli movimento e scorrimento nella sezione movimenti virtuali non sono funzionali. Il loro utilizzo non avrà alcun effetto. La tastiera virtuale nella stessa pagina funziona correttamente.
* Dopo aver abilitato la modalità sviluppatore in impostazioni, potrebbero essere necessari alcuni secondi prima che l'opzione per attivare il portale del dispositivo sia abilitata.

## <a name="api"></a>API
* Se l'applicazione imposta il [punto di messa a fuoco](focus-point-in-unity.md) dietro l'utente o il normale alla fotocamera. in futuro, gli ologrammi non verranno visualizzati in foto o video di acquisizione realtà mista. Fino a quando questo bug non viene risolto in Windows, se le applicazioni attivano attivamente il [punto di messa a fuoco](focus-point-in-unity.md) , è necessario assicurarsi che la normale del piano sia impostata in modo opposto rispetto alla fotocamera, ad esempio Normal =-camera. Inoltr.

## <a name="xbox-wireless-controller"></a>Controller wireless Xbox
* È necessario aggiornare i controller wireless Xbox prima di poterli usare con HoloLens. Assicurarsi di essere [aggiornati](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) prima di tentare di associare il controller a un HoloLens.
* Se si riavvia il HoloLens mentre il controller wireless Xbox è connesso, il controller non si riconnetterà automaticamente a HoloLens. La luce del pulsante della guida lampeggerà lentamente fino a quando il controller non si spegne dopo 3 minuti. Per riconnettere immediatamente il controller, spegnere il controller tenendo premuto il pulsante della guida fino a quando la luce non si spegne. Quando si accende nuovamente il controller, questo si riconnetterà a HoloLens.
* Se il HoloLens entra in standby mentre il controller wireless Xbox è connesso, qualsiasi input sul controller riattiverà il HoloLens. È possibile evitare questo problema spegnendo il controller al termine dell'uso.
