---
title: La posizione di modelli 3D nell'ambiente domestico
description: Come inserire i modelli 3D dal sito Web o applicazione in casa la realtà mista di Windows
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, model, sul posto nella home page, sul posto, mondo, modellazione, realtà mista home, web, app
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829730"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>La posizione di modelli 3D in realtà mista home

> [!NOTE]
> Questa funzionalità è stato aggiunto durante la [Windows 10 April 2018 Update](release-notes-april-2018.md). Le versioni precedenti di Windows non sono compatibili con questa funzionalità.

Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni. In alcuni scenari, le app 2D (ad esempio, l'app Vntana) la posizione di modelli 3D direttamente nella home page di realtà mista come decorazioni o per un'ulteriore l'ispezione in 3D completo. Il *Aggiungi modello protocollo* consente di inviare un modello 3D dal sito Web o all'applicazione direttamente nella realtà mista di Windows Home page, dove salverà come [nelle schermate di avvio app 3D](3d-app-launcher-design-guidance.md), App 2D e vntana. 

Ad esempio, se si sta sviluppando un'applicazione che espone un catalogo di 3D arredamento per la progettazione di uno spazio, è possibile usare la *Aggiungi modello protocollo* per consentire agli utenti di inserire tali modelli 3D mobili dal catalogo. Una volta inseriti nel mondo, gli utenti possono spostare, ridimensionare e rimuovere questi modelli 3D esattamente come altri vntana nella home page. Questo articolo offre una panoramica dell'implementazione di *aggiungere protocollo del modello* in modo che sia possibile iniziare consentendo agli utenti decorare il mondo con oggetti 3D da app o sul web.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Aggiungere il protocollo di modello</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Panoramica

Esistono 2 passaggi per abilitare il posizionamento dei modelli 3D in casa la realtà mista di Windows:
1. [Verificare che il modello 3D è compatibile con la realtà mista di Windows home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implementare il *Aggiungi modello protocollo* nell'applicazione o pagina Web (questo articolo).

## <a name="implementing-the-add-model-protocol"></a>Implementazione di *aggiungere protocollo del modello*

Dopo aver creato un [compatibile con modelli 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), è possibile implementare le *aggiungere protocollo del modello* attivando l'URI seguente da qualsiasi pagina Web o un'applicazione:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se l'URI punta a una risorsa remota, quindi verrà automaticamente scaricato e inserito nella home page. Le risorse locali verranno copiate alla cartella di dati di app di realtà mista domestico prima di essere inserito nella home page. È consigliabile progettare l'esperienza all'account per gli scenari in cui l'utente potrebbe essere in esecuzione una versione precedente di Windows che non supporta questa funzionalità se si nasconde il pulsante o disabilitando, se possibile. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Richiama il *Aggiungi modello protocollo* da un'app Universal Windows Platform:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Richiama il *Aggiungi modello protocollo* da una pagina Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerazioni per immersive auricolari (VR)

* Per immersive auricolari (VR), il portale di realtà mista non dispone sia in esecuzione prima di richiamare il *Aggiungi modello protocollo*. In questo caso, il *Aggiungi modello protocollo* avvierà il portale di realtà mista e porre l'oggetto direttamente in cui le cuffie necessita di una volta arrivati in realtà mista home. 
* Quando si richiama il *Aggiungi modello protocollo* dal desktop con il portale di realtà mista è già in esecuzione, assicurarsi che le cuffie sono "attivo". In caso contrario, la selezione host non riuscirà. 

## <a name="see-also"></a>Vedere anche

* [Creazione di modelli 3D per l'uso di casa di realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
