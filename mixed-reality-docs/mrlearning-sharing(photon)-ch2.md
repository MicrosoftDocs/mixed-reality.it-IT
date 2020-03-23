---
title: Esercitazioni sulle funzionalità multiutente - 2. Preparazione di Unity per lo sviluppo
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031233"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Preparazione di Unity per lo sviluppo

In questa esercitazione imparerai a preparare e configurare Unity per lo sviluppo di applicazioni, incluse l'importazione di Mixed Reality Toolkit, la configurazione delle impostazioni di compilazione e la preparazione della scena.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo di applicazioni
* Importare Mixed Reality Toolkit
* Preparare la scena del progetto

## <a name="instructions"></a>Istruzioni

1. Scarica e salva il pacchetto Mixed Reality Toolkit Foundation per Unity facendo clic [qui](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage).

2. In Unity fai clic sul menu Assets (Asset), scegli Import Package (Importa pacchetto) e quindi Custom Package (Pacchetto personalizzato).

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Seleziona il pacchetto per Unity scaricato dal collegamento fornito nel passaggio 1. Dopo che la finestra popup di importazione è stata visualizzata in Unity, fai clic sul pulsante Import (Importa) per iniziare a importare MRTK. Questa operazione può richiedere alcuni minuti.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Il pacchetto scaricato si trova nella cartella locale in cui hai salvato il file. L'immagine riportata sopra non indica la posizione in cui troverai il pacchetto.

    Dopo che il pacchetto è stato importato, dovrebbe venire visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, apri tale finestra scegliendo Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilità > Configura progetto Unity) dal menu Unity.

    Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione Modify Configurations (Modifica configurazioni), deseleziona la casella di controllo Enable MSBuild for Unity (Abilita MSBuild per Unity), verifica che tutte le altre opzioni siano selezionate e fai clic sul pulsante Apply (Applica) per applicare le impostazioni.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > MSBuild per Unity potrebbe non supportare tutti gli SDK che userai ed essere difficile da disabilitare dopo che è stato abilitato. Di conseguenza, è consigliabile non abilitare MSBuild per Unity.
    
4. Crea una nuova scena. A tale scopo, fai clic su File e scegli New Scene (Nuova scena). Salva la scena con il nome HLSharedProjectMain.

5. In Mixed Reality Toolkit fai clic su Add to Scene and Configure (Aggiungi alla scena e configura).

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Al termine, seleziona Mixed-Reality Toolkit (MRTK) nella gerarchia. Nel riquadro Inspector (Controllo) modifica il profilo di configurazione di MRTK in DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Seleziona Mixed-Reality Toolkit (MRTK) nella gerarchia. Nel riquadro Inspector (Controllo) cerca Mixed Reality Toolkit (Script) e premi il pulsante "Copy & Customize" (Copia e personalizza), come illustrato nella figura seguente.  Successivamente verrà visualizzata una finestra popup. Seleziona l'opzione Clone (Clona) nel menu a comparsa.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Scorri verso il basso e deseleziona Enable Diagnostics System (Abilita sistema di diagnostica) per nascondere la finestra di diagnostica. Consigliamo di mantenere abilitata la finestra di diagnostica durante lo sviluppo delle applicazioni per monitorare le prestazioni e quindi disabilitarla durante la produzione o le dimostrazioni delle applicazioni. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Per aprire le impostazioni di compilazione, premi CTRL+MAIUSC+B oppure passa a File->Build Settings (Impostazioni di compilazione). Si noti che il programma è attualmente impostato nella piattaforma autonoma PC, Mac e Linux. Per lo sviluppo HoloLens 2, imposta la piattaforma Universal Windows Platform. Selezionala e fai clic su Switch Platform (Cambia piattaforma).

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Al termine, fai clic sulla casella denominata Add Open Scenes (Aggiungi scene aperte). Passa ora al riquadro Inspector (Controllo) e verifica che la casella di controllo a destra di Virtual Reality Supported (Realtà virtuale supportata) (come illustrato nell'immagine seguente) sia selezionata. Verifica inoltre che sia selezionata anche la casella di controllo accanto a Scenes/HLSharedProjectMain, come illustrato nell'immagine seguente.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Nella sezione Publishing Settings (Impostazioni di pubblicazione) del riquadro Inspector (Controllo) scorri verso il basso fino a Capabilities (Funzionalità) e verifica che siano selezionate le caselle di controllo seguenti:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importa i pacchetti personalizzati elencati:

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versione 2.1.1)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Per rivedere la procedura di configurazione di un progetto Unity per Ancoraggi nello spazio di Azure, vedi l'esercitazione [Introduzione ad Ancoraggi nello spazio di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) che fa parte della serie di esercitazioni relative ad [Ancoraggi dello spazio di Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).


13. Nel riquadro Project (Progetto) passa alla cartella Prefabs (Prefab). Nei passaggi seguenti implementerai alcuni prefab nella scena. Nella cartella Prefabs (Prefab) fai clic e trascina il prefab DebugWindow nella gerarchia. Al termine, salva il progetto facendo clic su File e quindi su Save (Salva) oppure premendo CTRL+S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Potrai notare che, facendo clic sul prefab, viene visualizzata una finestra popup in cui vengono chieste informazioni su TMP Essentials. Fai clic su Import TMP Essentials (Importa TMP Essentials) perché è necessario. Se viene visualizzata questa finestra popup, potrebbe essere necessario eliminare il prefab dalla gerarchia e ritrascinarlo nella gerarchia per evitare potenziali errori correlati al testo.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle prossime esercitazioni svilupperemo questa scena e il progetto Unity per la realizzazione di un'esperienza condivisa completa.

[Esercitazione successiva: 3. Connessione di più utenti](mrlearning-sharing(photon)-ch3.md)
