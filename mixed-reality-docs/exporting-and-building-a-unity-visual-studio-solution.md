---
title: Esportazione e compilazione di una soluzione Unity di Visual Studio
description: Questo articolo illustra come esportare il progetto di realtà mista da Unity, in modo da poter compilare e distribuire in Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, Esporta, compila, Distribuisci
ms.openlocfilehash: 752a9dd002d27d24d9b80a1a97cb07a44237b9e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435570"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Esportazione e compilazione di una soluzione Unity di Visual Studio

Se non si prevede di usare la tastiera di sistema nell'applicazione, è consigliabile usare *D3D* perché l'applicazione userà una quantità di memoria leggermente inferiore e un tempo di avvio leggermente più rapido. Se si usa l'API TouchScreenKeyboard nel progetto per usare la tastiera di sistema, è necessario esportare come *XAML*.

## <a name="how-to-export-from-unity"></a>Come esportare da Unity

![impostazioni di compilazione Unity](images/unitybuildsettings-300px.png)<br>
*Impostazioni di compilazione Unity*

1. Quando si è pronti per esportare il progetto da Unity, aprire il menu **file** e selezionare **impostazioni di compilazione...**
2. Fare clic su **Aggiungi scene aperte** per aggiungere la scena alla compilazione.
3. Nella finestra di dialogo **impostazioni di compilazione** scegliere le opzioni seguenti per esportare per HoloLens:
   * **Piattaforma:** *piattaforma UWP (Universal Windows Platform)* e assicurarsi di selezionare **Switch Platform (Cambia piattaforma** ) per rendere effettive le selezioni.
   * **SDK:** *universale 10*.
   * **Tipo di compilazione UWP:** *D3D*.
4. **Facoltativo**: **progetti C# Unity:** selezionato.

>[!NOTE]
>Selezionando questa casella è possibile:
>* Eseguire il debug dell'app in Visual Studio Remote Debugger.
>* Modificare gli script nel progetto C# Unity usando IntelliSense per le API WinRT.

5. Dalla finestra **impostazioni di compilazione...** aprire **lettore impostazioni...**
6. Selezionare le **impostazioni per** la scheda piattaforma UWP (Universal Windows Platform).
7. Espandere il gruppo di **Impostazioni XR** .
8. Nella sezione **impostazioni di XR** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco di **dispositivi di realtà virtuale** e confermare che la **realtà mista di Windows** è elencata come un dispositivo supportato.
9. Tornare alla finestra di dialogo **impostazioni di compilazione** .
10. Selezionare **Compila**.
11. Nella finestra di dialogo Esplora risorse visualizzata creare una nuova cartella che contenga l'output di compilazione di Unity. In genere, la cartella "app" viene denominata.
12. Selezionare la cartella appena creata e fare clic su **Seleziona cartella**.
13. Una volta completata la compilazione di Unity, viene visualizzata una finestra di Esplora risorse per la directory radice del progetto. Passare alla cartella appena creata.
14. Aprire il file della soluzione di Visual Studio generato che si trova all'interno di questa cartella.

## <a name="when-to-re-export-from-unity"></a>Quando eseguire nuovamente l'esportazione da Unity

Se si selezionaC# la casella di controllo "progetti" quando si esporta l'app da Unity, viene creata una soluzione di Visual Studio che include tutti i file di script Unity. Ciò consente di eseguire l'iterazione degli script senza riesportare da Unity. Tuttavia, se si desidera apportare modifiche al progetto che non cambiano solo il contenuto degli script, sarà necessario eseguire di nuovo l'esportazione da Unity. Di seguito sono riportati alcuni esempi di casi in cui è necessario eseguire di nuovo l'esportazione da Unity:
* È possibile aggiungere o rimuovere asset nella scheda progetto.
* È possibile modificare qualsiasi valore nella scheda Inspector (controllo).
* Si aggiungono o rimuovono oggetti dalla scheda gerarchia.
* Modificare le impostazioni del progetto Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilazione e distribuzione di una soluzione Unity di Visual Studio

Il resto della compilazione e della distribuzione delle app avviene in [Visual Studio](using-visual-studio.md). Sarà necessario specificare una configurazione di compilazione Unity. Le convenzioni di denominazione di Unity possono essere diverse da quelle usate in genere in Visual Studio:

|  Configurazione  |  Spiegazione | 
|----------|----------|
|  Debug  |  Tutte le ottimizzazioni disattivate e il profiler è abilitato. Utilizzato per eseguire il debug degli script. | 
|  Master  |  Tutte le ottimizzazioni sono attivate e il profiler è disabilitato. Usato per inviare app allo Store. | 
|  Rilascia  |  Tutte le ottimizzazioni sono attivate e il profiler è abilitato. Usato per valutare le prestazioni dell'app. | 

Si noti che l'elenco precedente è un subset dei trigger comuni che comporteranno la generazione del progetto di Visual Studio. In generale, la modifica dei file con estensione cs da Visual Studio non richiede la rigenerazione del progetto da Unity.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se le modifiche apportate ai file con estensione cs non vengono riconosciute nel progetto di Visual Studio, assicurarsi che "progetti C# Unity" sia selezionato quando si genera il progetto vs dal menu Compila di Unity.
