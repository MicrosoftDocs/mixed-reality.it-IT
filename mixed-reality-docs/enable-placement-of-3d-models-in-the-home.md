---
title: Abilitare la selezione host dei modelli 3D nella Home page
description: Come inserire modelli 3D dal sito Web o dall'applicazione nella Home realtà mista di Windows
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modello, posizione in casa, luogo, mondo, modellazione, Home realtà mista, Web, app
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829730"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Abilitare la selezione host dei modelli 3D nella Home realtà mista

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md). Le versioni precedenti di Windows non sono compatibili con questa funzionalità.

La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni. In alcuni scenari, le app 2D, ad esempio l'app Olografics, consentono di posizionare i modelli 3D direttamente nella Home realtà mista come decorazioni o per un ulteriore controllo in 3D completo. Il *protocollo Aggiungi modello* consente di inviare un modello 3D dal sito Web o dall'applicazione direttamente nella Home realtà mista di Windows, in cui verrà mantenuto come i [lanci di app 3D](3d-app-launcher-design-guidance.md), le app 2D e gli ologrammi. 

Se, ad esempio, si sta sviluppando un'applicazione che espone un catalogo di mobili 3D per la progettazione di uno spazio, è possibile usare il *protocollo Aggiungi modello* per consentire agli utenti di collocare i modelli di mobili 3D dal catalogo. Una volta inserite in tutto il mondo, gli utenti possono spostare, ridimensionare e rimuovere questi modelli 3D esattamente come altri ologrammi nella Home page. Questo articolo fornisce una panoramica dell'implementazione del *protocollo Add Model* in modo da consentire agli utenti di decorare il proprio mondo con oggetti 3D dall'app o dal Web.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Aggiungi protocollo modello</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Panoramica

Per abilitare il posizionamento dei modelli 3D nella Home realtà mista di Windows sono necessari due passaggi:
1. [Verificare che il modello 3D sia compatibile con la Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implementare il *protocollo Aggiungi modello* nell'applicazione o nella pagina Web (questo articolo).

## <a name="implementing-the-add-model-protocol"></a>Implementazione del *protocollo Add Model*

Quando si dispone di un [modello 3D compatibile](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), è possibile implementare il *protocollo Add Model* attivando l'URI seguente da qualsiasi pagina Web o applicazione:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Se l'URI punta a una risorsa remota, verrà automaticamente scaricato e inserito nella Home page. Le risorse locali verranno copiate nella cartella di dati dell'app della Home realtà mista prima di essere inserite nella Home page. Si consiglia di progettare un'esperienza per gli scenari in cui l'utente potrebbe eseguire una versione precedente di Windows che non supporta questa funzionalità nascondendo il pulsante o disabilitando l'operazione, se possibile. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Richiamo del *protocollo Add Model* da un'app piattaforma UWP (Universal Windows Platform):

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Richiamo del *protocollo di aggiunta modello* da una pagina Web:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Considerazioni per auricolari immersivi (VR)

* Per gli auricolari immersivi (VR), non è necessario che il portale per la realtà mista sia in esecuzione prima di richiamare il *protocollo di aggiunta del modello*. In questo caso, il *protocollo Add Model* avvierà il portale di realtà mista e inserirà l'oggetto direttamente nel punto in cui l'auricolare sta cercando una volta arrivati nella Home realtà mista. 
* Quando si richiama il *protocollo Aggiungi modello* dal desktop con il portale per la realtà mista già in esecuzione, assicurarsi che l'auricolare sia "sveglio". In caso contrario, la selezione host non avrà esito positivo. 

## <a name="see-also"></a>Vedere anche

* [Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
