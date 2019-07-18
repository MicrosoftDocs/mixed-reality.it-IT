---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 3e4be00ddeab6d91dbbc8226bfa3dc543cded095
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293688"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Condivisione di movimenti di oggetti con più utenti

In questa esercitazione si apprenderà come condividere i movimenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa possano collaborare insieme e visualizzare le interazioni degli altri. Questa lezione si basa sull'utilità di avvio lunare compilata come parte delle esercitazioni sul [modulo di base](mrlearning-base.md).

Obiettivi

- Portare il Launcher Lunar come modello 3D da condividere
- Configurare il progetto in modo da condividere i movimenti del modello 3D.
- Informazioni su come creare un'applicazione di collaborazione multiutente di base

### <a name="instructions"></a>Istruzioni


1. Salvare la scena dalla lezione precedente (CTRL + S). È possibile denominarlo, HLSharedProjectMainPart4. Unity, in modo che sia più facile da trovare quando è necessario.

2. Dalla finestra del progetto, nella cartella Asset-> Scripts, fare doppio clic su GenericNetSync per aprirlo in Visual Studio o in cui si usa l'editor di codice.  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Nelle righe 34 e 38 rimuovere il//per attivare il codice per la tabella che verrà usata in questa lezione. Salvare quindi il file. 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Nella finestra del progetto fare doppio clic sul file PhotonRoom.cs nella cartella assets-> Scripts per aprirlo in Visual Studio. 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Proprio come nel passaggio 3, è necessario rimuovere il//per attivare il codice alle righe 25, 26 e 106.

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Nella visualizzazione gerarchia selezionare l'oggetto NetworkRoom.

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates. Prima di tutto, trascinare e rilasciare la tabella prefabbricata nello slot Tableprefab della classe PhotonRoom. Trascinare quindi la prefabbricazione LunarModule nello slot prefabbricato del modulo nella classe PhotonRoom.

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   Nota: Se si fa clic su uno degli oggetti prefabbricati e sulla versione, il controllo passerà a tale oggetto. Fare clic, trascinare, rilasciare e rilasciare ogni oggetto nello slot appropriato.

8. Fare clic sulla freccia a sinistra di MixedRealityPlayspace, quindi spostare l'oggetto Game figlio MainCamera nel prefabbricato SharedPlayground. A questo punto, eliminare il prefabbricato, MixedRealityPlayspace, da eliminare, selezionare il prefabbricato e toccare "Elimina" sulla tastiera.
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>Nota:  Verificare che entrambe le posizioni della fotocamera principale e del SharedPlayground siano impostate su 0, 0, 0.
>

9. Creare un nuovo set di oggetti di gioco come oggetto figlio per l'oggetto padre SharedPlayground per creare un nuovo oggetto. Fare clic con il pulsante destro del mouse sull'oggetto padre e selezionare Crea vuoto. 

10. Con il nuovo oggetto selezionato nella gerarchia, modificare il nome dell'oggetto in TableAnchor nel pannello Inspector. Inoltre, fare clic su Aggiungi componente e cercare il componente TableAnchor. Selezionarlo e aggiungerlo all'oggetto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Nota: Impostare il posizionamento su x = 1, y =-0,55 e z = 2. Inoltre, impostare la rotazione su y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. A questo punto, dal pannello del progetto nella cartella prefabbricates trascinare la tabella prefabbricata nell'oggetto figlio "TableAnchor" appena creato.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. Infine, nell'oggetto DebugWindow, impostare la larghezza su 50 e l'altezza su 20.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>Lezione completata


Al termine di questa operazione, tutti gli utenti che partecipano al progetto Unity possono spostare l'avvio Lunar. Tutti i movimenti sono sincronizzati in modo che ogni utente possa visualizzare le interazioni di ogni altro utente. Questi concetti servono come blocchi predefiniti fondamentali per esperienze di collaborazione condivise complete. 

Anche se tutti gli utenti sono connessi come parte di un'esperienza condivisa e possono visualizzare i movimenti relativi degli oggetti, l'applicazione non è ancora in grado di allineare in modo accurato gli avatar e gli oggetti in modo che gli utenti locali vedano gli altri oggetti e nella stessa posizione all'interno del computer fisico mondo. Per ancorare un'esperienza condivisa locale, ogni dispositivo richiede una conoscenza comune dell'ambiente fisico. In questo modulo questa operazione verrà eseguita usando gli [ancoraggi spaziali di Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) che saranno implementati nella lezione successiva.

Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA che copre le nozioni di base di ASA, la creazione di account e risorse di Azure e altri blocchi fondamentali per gli edifici necessari prima che sia possibile integrarli nell'esperienza condivisa.

[Lezione successiva: Lezione 5 della condivisione (Photon)](mrlearning-sharing(photon)-ch5.md)

