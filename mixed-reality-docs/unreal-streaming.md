---
title: Streaming in Unreal
description: Guida allo streaming in Unreal per HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, streaming, PC, app remota olografica, holographic remoting player, documentazione
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303532"
---
# <a name="streaming-in-unreal"></a>Streaming in Unreal

## <a name="overview"></a>Panoramica
Lo streaming da un PC a HoloLens offre due vantaggi fondamentali: 
* Consente all'app di realtà mista di sfruttare la potenza di calcolo del PC. 
* Consente di accelerare l'iterazione dello sviluppo. 

Prima di tutto, devi scaricare [Holographic Remoting Player](holographic-remoting-player.md) nel dispositivo HoloLens. Questo consente all'app di trasmettere direttamente in streaming al lettore remoto in HoloLens dalle origini seguenti:

* Editor Unreal Engine
* Un eseguibile Windows in pacchetto 

Durante lo streaming, hai accesso a quasi tutte le funzionalità di HoloLens che avresti a disposizione durante l'esecuzione di un'applicazione in un dispositivo. Questo include [tracciamento mano e articolazioni](unreal-hand-tracking.md) (se usi HoloLens 2), [mapping spaziale](unreal-spatial-mapping.md) e [ancoraggi nello spazio](unreal-spatial-anchors.md), ma esclude le funzionalità riportate in questo [elenco di limitazioni](holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * La qualità dello streaming dipende in larga misura dalla potenza del segnale Wi-Fi.
> * Tutte le funzionalità vengono abilitate automaticamente per il lettore Holographic Remoting. Se si trova una funzionalità che richiede l'autorizzazione dell'utente (ad esempio, il tracciamento oculare) per il funzionamento sul flusso ma non durante l'esecuzione nel dispositivo, verificare di aver abilitato le funzionalità appropriate nelle impostazioni del progetto.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origine</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Visori VR immersive</strong></td>
    </tr>
     <tr>
        <td>Editor Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Pacchetto Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming dall'editor Unreal

In qualità di sviluppatore, noterai che lo streaming dall'editor Unreal al dispositivo HoloLens offre grandi vantaggi in fase di test, ovvero non è più necessario attendere che l'app venga compilata e distribuita prima di provare gli aggiornamenti.

Puoi trovare istruzioni dettagliate sullo [streaming dall'editor Unreal](unreal-uxt-ch6.md#device-only-streaming) nell'ultima sezione della serie di esercitazioni di introduzione a Unreal.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming da un eseguibile Windows in pacchetto

A partire da Unreal 4.25.1, è possibile trasmettere l'app in streaming a un dispositivo HoloLens 2 da un eseguibile Windows in pacchetto seguendo questa procedura: 

1. Passa a **File > Package Project > Windows** (File > Crea pacchetto progetto > Windows) nel menu dell'editor. 
    * Scegli una posizione in cui salvare il pacchetto e fai clic su **Select Folder** (Seleziona cartella).

2. Terminata la creazione del pacchetto, apri **Holographic Remoting Player** in HoloLens 2 e prendi nota dell'indirizzo IP. 
3. Lascia aperto **Holographic Remoting Player** e usa il prompt della riga di comando per: 
    * accedere con cd alla directory locale in cui hai salvato il pacchetto.
    * Immettere il comando seguente: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> Dovrebbe essere usato automaticamente il nome dell'applicazione nelle impostazioni del progetto per creare il pacchetto di Windows. Se per qualche motivo sono diversi, usa il nome dell'eseguibile di Windows al prompt dei comandi.

Premi INVIO e inizierà lo streaming dell'applicazione.

## <a name="see-also"></a>Vedere anche
* [Cronologia delle versioni di Holographic Remoting](holographic-remoting-version-history.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](holographic-remoting-create-player.md)
* [Stabilire una connessione sicura con Holographic Remoting](holographic-remoting-secure-connection.md)
