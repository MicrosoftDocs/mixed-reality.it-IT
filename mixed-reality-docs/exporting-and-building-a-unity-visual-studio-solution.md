---
title: Esportazione e creazione di una soluzione di Visual Studio a Unity
description: Questo articolo illustra l'esportazione del progetto di realtà mista da Unity in modo che è possibile compilare e distribuire in Visual Studio.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, visual studio, esportare, compilare, distribuire
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603699"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Esportazione e creazione di una soluzione di Visual Studio a Unity

Se non si prevede sull'utilizzo della tastiera di sistema nell'applicazione, è consigliabile usare *D3D* come l'applicazione verrà Usa leggermente meno memoria e hanno un'ora di avvio leggermente più veloce. Se si usa l'API TouchScreenKeyboard nel progetto per usare la tastiera del sistema, è necessario esportare *XAML*.

## <a name="how-to-export-from-unity"></a>Come esportare da Unity

![Impostazioni di compilazione Unity](images/unitybuildsettings-300px.png)<br>
*Impostazioni di compilazione Unity*

1. Quando si è pronti per esportare il progetto di Unity, aprire il **File** dal menu **Build Settings...**
2. Fare clic su **aggiungere scene Open** per aggiungere la scena della compilazione.
3. Nel **Build Settings** finestra di dialogo, scegliere le opzioni seguenti per esportare per HoloLens:
   * **Piattaforma:** *Piattaforma Windows Universal* e assicurarsi di selezionare **commutatore piattaforma** per la selezione rendere effettive.
   * **SDK:** *10 universale*.
   * **Tipo di compilazione UWP:** *D3D*.
4. **Facoltativo**: **Unity C# progetti:** Controllati.

>[!NOTE]
>Selezionando questa casella di controllo consente di:
>* Eseguire il debug dell'app nel debugger remoto di Visual Studio.
>* Modificare gli script di Unity C# progetto quando si Usa IntelliSense for APIs WinRT.

5. Dal **le impostazioni di compilazione...**  finestra, aprire **le impostazioni del giocatore...**
6. Selezionare il **le impostazioni per la Universal Windows Platform** scheda.
7. Espandere la **XR impostazioni** gruppo.
8. Nel **impostazioni XR** sezione controllo il **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **dispositivi per realtà virtuale** elenco e confermare **"Windows misto Realtà"** viene elencato come un dispositivo supportato.
9. Tornare al **Build Settings** finestra di dialogo.
10. Selezionare **compilazione**.
11. Nella finestra di dialogo Esplora Windows che viene visualizzato creare una nuova cartella per contenere l'output di compilazione di Unity. In genere, si denominare la cartella "App".
12. Selezionare la cartella appena creata e fare clic su **selezionare la cartella**.
13. Una volta Unity ha terminato la compilazione, verrà aperta una finestra di Windows Explorer alla directory radice del progetto. Passare alla cartella appena creata.
14. Aprire il file di soluzione Visual Studio generato che si trova all'interno della cartella.

## <a name="when-to-re-export-from-unity"></a>Casi in cui esportare nuovamente da Unity

Verifica il "C# progetti di" casella di controllo quando l'esportazione di app da Unity crea una soluzione di Visual Studio che include tutti i file di script di Unity. In questo modo è possibile scorrere gli script senza esportare nuovamente da Unity. Tuttavia, se si desidera apportare modifiche al progetto che non vengono semplicemente modificando il contenuto degli script, dovrai ripetere l'esportazione da Unity. Sono riportati alcuni esempi di volte in cui che è necessario ripetere l'esportazione da Unity
* Aggiungere o rimuovere gli asset nella scheda progetti.
* Modificare qualsiasi valore nella scheda di controllo.
* Per aggiungere o rimuovere oggetti dalla scheda della gerarchia.
* Si modificano le impostazioni di progetto Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilazione e distribuzione di una soluzione di Visual Studio a Unity

Si verifica il resto della compilazione e distribuzione di App in [Visual Studio](using-visual-studio.md). È necessario specificare una configurazione della build Unity. Convenzioni di denominazione di Unity potrebbero essere diversi da quello che si sta in genere usato per Visual Studio:

|  Configurazione  |  Spiegazione | 
|----------|----------|
|  Debug  |  Tutte le ottimizzazioni disattivato e il profiler è abilitato. Utilizzato per il debug degli script. | 
|  Master  |  Tutte le ottimizzazioni vengono attivate e il profiler è disabilitato. Utilizzato per inviare le app di Store. | 
|  Rilascio  |  Tutte le ottimizzazioni vengono attivate e il profiler sia abilitato. Utilizzato per valutare le prestazioni delle app. | 

Si noti che l'elenco riportato sopra è un subset dei trigger comuni che determinano il progetto di Visual Studio devono essere generati. In generale, la modifica dei file con estensione cs all'interno di Visual Studio non è necessario il progetto per essere rigenerato da all'interno di Unity.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si ritiene che le modifiche ai file con estensione cs non vengono riconosciute nel progetto di Visual Studio, assicurarsi che "Unity C# progetti" è selezionato quando si genera il progetto di Visual Studio dal menu di compilazione di Unity.
