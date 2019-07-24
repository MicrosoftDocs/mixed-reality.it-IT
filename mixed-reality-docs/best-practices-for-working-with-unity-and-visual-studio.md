---
title: Procedure consigliate per l'utilizzo di Unity e Visual Studio
description: Suggerimenti e consigli per semplificare il flusso di lavoro della creazione di un'applicazione di realtà mista con Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Deploy, Unity, Visual Studio, HoloLens, HoloLens 2, Full-Headset
ms.openlocfilehash: b2c345a8cc9bddcbc447531eb5f6cdacc62f2e98
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522318"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedure consigliate per l'utilizzo di Unity e Visual Studio

Uno sviluppatore che crea un'applicazione di realtà mista con Unity dovrà passare tra Unity e Visual Studio per creare il pacchetto dell'applicazione distribuito in HoloLens e/o un auricolare immersivo. Per impostazione predefinita, sono necessarie due istanze di Visual Studio (una per modificare gli script Unity e una per la distribuzione nel dispositivo e il debug). La procedura seguente consente lo sviluppo usando una singola istanza di Visual Studio, riduce la frequenza di esportazione dei progetti Unity e migliora l'esperienza di debug.

## <a name="improving-iteration-time"></a>Miglioramento del tempo di iterazione

Il supporto per il back-end di scripting .NET in Unity è stato deprecato in Unity 2018 e rimosso in Unity 2019 +. Si consiglia quindi di passare a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). Questa operazione può tuttavia comportare tempi di compilazione più lunghi da Unity a Visual Studio. Per migliorare l'iterazione più veloce, è necessario configurare l'ambiente per ottenere risultati ottimali per la compilazione.

1) Utilizzare la compilazione incrementale compilando il progetto nella stessa directory ogni volta, riutilizzando i file predefiniti
2) Disabilitare le analisi del software anti-malware per il progetto & cartelle di compilazione
   - Aprire **Virus & Threat Protection** nell'app impostazioni di Windows 10
   - Selezionare **Gestisci impostazioni** in **virus & impostazioni di protezione dalle minacce**
   - Selezionare **Aggiungi o Rimuovi esclusioni** nella sezione **esclusioni**
   - Fare clic su **Aggiungi un'esclusione** e selezionare la cartella che contiene il codice del progetto Unity e gli output di compilazione
3) Usare un'unità SSD per la compilazione

Per altre informazioni, vedere [ottimizzazione dei tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) . Vedere anche [debug per il back-end di scripting di IL2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Si consiglia inoltre di installare l' [estensione *UnityScriptAnalyzer* di Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Questo strumento analizza gli script Unity C# per il codice che può essere scritto in modo più ottimizzato.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity

Scarica [Visual Studio Tools per Unity](https://docs.microsoft.com/en-us/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Vantaggi di Visual Studio Tools per Unity**
* Eseguire il debug della modalità di riproduzione in-editor di Unity da Visual Studio inserendo punti di interruzione, valutando variabili ed espressioni complesse.
* Usare Esplora progetti Unity per trovare lo script con la stessa gerarchia visualizzata da Unity.
* Ottenere la console Unity direttamente all'interno di Visual Studio.
* Utilizzare le procedure guidate per creare o esplorare rapidamente gli script.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Esporre C# le variabili di classe per semplificare l'ottimizzazione

Esistono due modi per esporre le variabili di classe. Il modo consigliato per eseguire questa operazione consiste nell'aggiungere l'attributo [SerializeField] alle variabili private. In questo modo, è possibile accedervi dall'editor, ma non a livello esposti.  L'altra opzione consiste nel rendere C# pubbliche le variabili di classe per esporle nell'interfaccia utente dell'editor. 

Entrambi gli approcci consentono di modificare facilmente le variabili durante la riproduzione in-Editor. Questa operazione è particolarmente utile per l'ottimizzazione delle proprietà meccaniche di interazione.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Rigenera le soluzioni di Visual Studio UWP dopo l'aggiornamento di Windows SDK o Unity

Le soluzioni di Visual Studio UWP archiviate nel controllo del codice sorgente possono essere aggiornate dopo l'aggiornamento a un nuovo motore di Windows SDK o Unity. È possibile risolvere questo problema dopo l'aggiornamento compilando una nuova soluzione UWP da Unity, quindi unendo eventuali differenze nella soluzione archiviata.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usare asset in formato testo per facilitare il confronto delle modifiche del contenuto

L'archiviazione di asset in formato testo rende più semplice la verifica delle differenze delle modifiche del contenuto in Visual Studio. È possibile abilitare questa impostazione in "Modifica > Impostazioni progetto > Editor" modificando la modalità di **serializzazione asset** per forzare il **testo**. Tuttavia, l'Unione delle modifiche dei file di asset di testo è soggetta a errori e non è consigliata, quindi è consigliabile abilitare estrazioni binarie esclusive nel sistema di controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Visual Studio Tools per Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Ottimizzazione dei tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Estensione di Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)