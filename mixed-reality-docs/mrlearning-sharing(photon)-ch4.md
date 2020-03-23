---
title: Esercitazioni sulle funzionalità multiutente - 4. Condivisione dei movimenti di oggetti con più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031252"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Condivisione dei movimenti di oggetti con più utenti

In questa esercitazione imparerai a condividere i movimenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa possano collaborare e visualizzare le interazioni reciproche. Questa lezione si basa sull'uso del modulo lunare creato durante le [esercitazioni relative al modulo di base](mrlearning-base.md).

## <a name="objectives"></a>Obiettivi

- Introdurre il modulo lunare come modello 3D da condividere
- Configurare il progetto per condividere i movimenti del modello 3D
- Imparare a creare un'applicazione collaborativa multiutente di base

## <a name="instructions"></a>Istruzioni

1. Salva la scena della lezione precedente (CTRL+S). Puoi denominarla HLSharedProjectMainPart4.unity per poterla trovare più facilmente in caso di necessità.

2. Nella finestra Project (Progetto), nella cartella Assets->Scripts (Asset->Script), fai doppio clic su GenericNetSync per aprirlo in Visual Studio o in qualsiasi editor di codice in uso.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Nelle righe 34 e 38 rimuovi "//" per attivare il codice della tabella che userai in questa lezione. Salva quindi il file.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Nella finestra Project (Progetto) fai doppio clic sul file PhotonRoom.cs nella cartella Assets->Scripts (Asset->Script) per aprirlo in Visual Studio.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Come nel passaggio 3, dobbiamo rimuovere "//" per attivare il codice nelle righe 25, 26 e 106.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Nella visualizzazione Hierarchy (Gerarchia) seleziona l'oggetto NetworkRoom.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Nella visualizzazione Project (Progetto) passa ad Assets->Resources->Prefabs (Asset->Risorse->Prefab). Trascina prima il prefab Table nello slot Tableprefab della classe PhotonRoom. Trascina quindi RocketLauncherCompleteVariantprefab nello slot Module Prefab della classe PhotonRoom.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Se fai clic su uno degli oggetti prefab e lo rilasci, in Inspector (Controllo) verrà visualizzato tale oggetto. Fai clic, trascina e rilascia ogni oggetto nello slot appropriato.

8. Fai clic sulla freccia a sinistra di MixedRealityPlayspace e sposta l'oggetto gioco figlio MainCamera in basso nel prefab SharedPlayground. Successivamente, elimina il prefab MixedRealityPlayspace selezionandolo e toccando "CANC" sulla tastiera.

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Verifica che le posizioni di MainCamera e SharedPlayground siano entrambe impostate su 0,0,0.

9. Seleziona l'oggetto "SharedPlayground" e fai clic con il pulsante destro del mouse per scegliere l'opzione "Create Empty" (Crea vuoto) e creare un oggetto gioco vuoto come figlio dell'oggetto gioco "SharedPlayground".

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Con il nuovo oggetto selezionato nella gerarchia, modifica il nome dell'oggetto in TableAnchor nel riquadro Inspector (Controllo). Inoltre, fai clic su Add Component (Aggiungi componente) e cerca il componente TableAnchor. Selezionalo e aggiungilo all'oggetto.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. Nel riquadro Project (Progetto) della cartella Prefabs (Prefab) trascina il prefab Table nell'oggetto figlio "TableAnchor" appena creato.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>Lezione completata

Al termine, cerca il modulo lunare. Successivamente, tutti gli utenti che partecipano al progetto Unity potranno spostare il modulo lunare.  Tutti i movimenti vengono sincronizzati in modo che ogni utente possa vedere le interazioni reciproche. Questi concetti costituiscono i blocchi predefiniti fondamentali per esperienze di collaborazione complete e condivise.

Anche se tutti gli utenti sono connessi nell'ambito di un'esperienza condivisa e possono vedere i movimenti relativi degli oggetti, l'applicazione non è ancora in grado di allineare in modo preciso avatar e oggetti, tanto che gli utenti locali non sono in grado di vedersi e di vedere gli oggetti nella stessa posizione all'interno del mondo fisico. Per ancorare un'esperienza condivisa locale, tutti i dispositivi devono avere una comune comprensione dell'ambiente fisico. A questo scopo, in questo modulo useremo [Ancoraggi nello spazio di Azure](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) che verrà implementato nella prossima lezione.

Prima di procedere con la prossima lezione, dobbiamo completare il modulo di apprendimento di ASA, che comprende le nozioni di base di ASA, la creazione di risorse e account di Azure, nonché altri blocchi predefiniti fondamentali, necessari per l'integrazione nell'esperienza condivisa.

[Lezione successiva: 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mrlearning-sharing(photon)-ch5.md)
