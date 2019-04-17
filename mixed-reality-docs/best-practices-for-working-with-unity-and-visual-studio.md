---
title: Le procedure consigliate per l'uso di Unity e Visual Studio
description: Suggerimenti e consigli per ottimizzare il flusso di lavoro di creazione di un'applicazione di realtà mista con Unity e Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: distribuire, unity, visore VR immersivi visual studio, HoloLens,
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604107"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Le procedure consigliate per l'uso di Unity e Visual Studio

Uno sviluppatore che crea un'applicazione di realtà mista con Unity sarà necessario passare tra Unity e Visual Studio per compilare il pacchetto di applicazione che viene distribuito a HoloLens e/o un visore VR immersivi. Per impostazione predefinita due istanze di Visual Studio sono necessario (uno per modificare gli script di Unity) e uno per distribuire il dispositivo ed eseguire il debug. La procedura seguente consente di sviluppare usando una singola istanza di Visual Studio, si riduce la frequenza di esportazione i progetti Unity e migliora l'esperienza di debug.

## <a name="improving-iteration-time"></a>Riducendo i tempi di iterazione

Un problema comune del flusso di lavoro quando si lavora con Unity e Visual Studio è la presenza di più finestre di Visual Studio aperto e dover costantemente passare da Visual Studio e Unity per eseguire l'iterazione.
1. **Unity** - per la modifica della scena e l'esportazione di una soluzione di Visual Studio
2. **Visual Studio (1)** - per la modifica di script
3. **Visual Studio (2)** : per compilazione e distribuzione di Unity esportato soluzione di Visual Studio al dispositivo

Per fortuna, vi è un modo per semplificare a una singola istanza di Visual Studio e ridurre le esportazioni frequenti da Unity.

Quando [esportazione del progetto di Unity](exporting-and-building-a-unity-visual-studio-solution.md), selezionare la **Unity C# progetti** casella di controllo nel menu "File > Build Settings". A questo punto, il progetto si esporta da Unity include tutto il progetto C# gli script e presenta diversi vantaggi:
* Usare la stessa istanza di Visual Studio per la scrittura di script e compilazione/distribuzione del progetto
* Esportazione da Unity solo quando la scena viene modificata nell'Editor di Unity; modifica il contenuto degli script può essere eseguita in Visual Studio senza esportare nuovamente.

Con **Unity C# progetti** abilitato, è necessario aprire solo un'istanza di ogni programma:
1. **Unity** - per la modifica della scena e l'esportazione di una soluzione di Visual Studio
2. **Visual Studio** : per la modifica di script, quindi compilazione e distribuzione di Unity esportato soluzione di Visual Studio al dispositivo

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools per Unity

Scaricare [Visual Studio Tools per Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Vantaggi di Visual Studio Tools per Unity**
* Eseguire il debug in modalità play nell'editor di Unity da Visual Studio inserisce i punti di interruzione, valutare variabili ed espressioni complesse.
* Usare Esplora progetti Unity per trovare lo script con la stessa gerarchia esatta che Unity consente di visualizzare.
* Ottenere la console di Unity direttamente all'interno di Visual Studio.
* Usare le procedure guidate per creare rapidamente o passare agli script.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Esporre C# classe di variabili per l'ottimizzazione semplice

Esistono due modi per esporre le variabili di classe. Il metodo consigliato per eseguire questa operazione consiste nell'aggiungere l'attributo [SerializeField] per le variabili private. Ciò consente loro di essere accessibile dall'editor ma non a livello di codice esposti.  L'altra opzione consiste nell'apportare C# classe variabili pubbliche per poterle esporre nell'editor dell'interfaccia utente. 

Entrambi gli approcci consentono di modificare facilmente le variabili durante il gioco nell'editor. Ciò è particolarmente utile per ottimizzare le proprietà meccanico di interazione.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Rigenerare le soluzioni di piattaforma UWP Visual Studio dopo l'aggiornamento di Windows SDK o Unity

Soluzioni di piattaforma UWP Visual Studio archiviate nel controllo del codice sorgente possono ottenere non aggiornate dopo l'aggiornamento a un nuovo motore di Windows SDK o Unity. Si può risolvere questo problema dopo l'aggiornamento, creare una nuova soluzione di piattaforma UWP da Unity, quindi l'unione di eventuali differenze nella soluzione di archiviazione.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usare asset di formato di testo per un semplice confronto delle modifiche del contenuto

Archiviare gli asset in formato testo rende più semplice esaminare diff di modifica del contenuto in Visual Studio. A tale scopo, in "Modifica > progetto Impostazioni > Editor" modificando **Asset serializzazione** modalità **forzare il testo**. Tuttavia, le modifiche ai file di testo asset l'unione è soggetta a errori e pertanto non è consigliabile, provare ad abilitare estrazioni binario in modo esclusivo nel sistema di controllo origine.
