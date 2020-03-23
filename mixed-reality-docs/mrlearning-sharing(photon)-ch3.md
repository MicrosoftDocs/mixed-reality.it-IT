---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031223"
---
# <a name="3-connecting-multiple-users"></a>3. Connessione di più utenti

In questa lezione impareremo a connettere più utenti all'interno di un'esperienza live condivisa. Al termine di questa lezione, sarai in grado di aprire l'applicazione in più dispositivi e visualizzare l'avatar, rappresentato da una sfera per ogni persona che partecipa.

## <a name="objectives"></a>Obiettivi

* Configurare PUN all'interno dell'applicazione
* Configurare i giocatori
* Imparare a connettere più utenti in un'esperienza condivisa

## <a name="instructions"></a>Istruzioni

1. Nella cartella Assets->Resources->Prefabs (Asset->Risorse->Prefab) del riquadro Project (Progetto) trascina il prefab NetworkLobby selezionato nella gerarchia, come illustrato nell'immagine seguente.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando espandi NetworkLobby, verrà visualizzato un oggetto figlio denominato NetworkRoom. Con NetworkRoom selezionato, passa al riquadro Inspector (Controllo) e fai clic su Add Component (Aggiungi componente). Cerca PhotonView e aggiungi il componente.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crea un nuovo oggetto gioco vuoto nella gerarchia. Fai clic con il pulsante destro del mouse nella gerarchia e scegli Empty (Vuoto) dal menu di scelta rapida. Verifica che il posizionamento sia impostato su x = 0, y = 0, z = 0 e assegna all'oggetto il nome PhotonUser.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Fai clic su Add Component (Aggiungi componente) e digita Generic Net Sync. Seleziona la classe Generic Net Sync (Sincronizzazione rete generica). Quando la classe viene visualizzata, fai clic sulla casella di controllo User (Utente) per attivarla.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Fai di nuovo clic su Add Component (Aggiungi componente) e digita Photon View. Seleziona la classe Photon View (Visualizzazione Photon) visualizzata nell'elenco a discesa.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Fai clic sull'icona File relativa alla classe Generic Net Sync (Sincronizzazione rete generica). Seleziona e trascina tale icona nel campo Observed Components (Componenti osservati) di Photon View (Visualizzazione Photon).

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. Successivamente, creiamo sfere che rappresentano ogni persona che partecipa a un'esperienza condivisa. Fai clic con il pulsante destro del mouse sull'oggetto PhotonUser creato, scorri verso il basso fino a 3D Object (Oggetto 3D) e scegli Sphere (Sfera). Verrà creato un oggetto gioco a forma di sfera come elemento figlio dell'oggetto PhotonUser.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Ridimensiona la sfera a x = 0,06, y = 0,06 e z = 0,06.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Trascina l'oggetto gioco PhotonUser nella cartella Prefabs (Prefab) del riquadro Project (Progetto) e quindi eliminalo dalla scena. Hai ora creato un prefab che può essere usato durante la generazione o la creazione di istanze di nuovi giocatori nell'ambito di un'esperienza condivisa.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >Verifica che l'oggetto gioco sia stato copiato nella cartella Prefabs (Prefab) prima di eliminarlo dalla gerarchia.

10. Crea un nuovo oggetto nella gerarchia seguendo le istruzioni fornite nel passaggio 3 e assegna a tale oggetto il nome SharedPlayground. Fai quindi clic su Add Component (Aggiungi componente) e cerca Generic Network Manager (Gestione rete generica).  Fai clic di nuovo per aggiungere il componente Generic Network Manager (Gestione rete generica). Modifica la posizione dell'oggetto in x = 0, y = 0 e z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>Lezione completata

Dopo aver completato tutti i passaggi precedenti e il processo di compilazione, premi il pulsante Play (Esegui) e connetti il dispositivo HoloLens 2. Vedrai una sfera che si muove quando muovi la testa. Tale oggetto verrà visualizzato per qualsiasi utente che partecipa al progetto Unity.

[Lezione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch4.md)
