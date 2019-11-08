---
title: Sguardo fisso e commit
description: Panoramica del modello di input sguardo fisso e commit
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: tracciamento oculare, realtà mista, input, sguardo fisso, selezione oculare della destinazione, HoloLens 2, selezione con gli occhi
ms.openlocfilehash: 89f5031635f2b67ba4c9afdf605559c2b9da4ac2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437827"
---
# <a name="eye-gaze-and-commit"></a>Sguardo fisso e commit
_Sguardo fisso e commit_ è un caso speciale del modello di input [sguardo e commit](gaze-and-commit.md) in base al quale viene selezionato come destinazione un oggetto mediante un semplice sguardo e viene eseguita un'azione sull'oggetto con un input di _commit_ secondario quale un movimento della mano, un comando vocale o un input da un dispositivo periferico, ad esempio da una periferica di gioco. 

Con HoloLens 2 hai l'incredibile opportunità di eseguire la sequenza _sguardo e commit_ in modo più rapido e pratico usando lo sguardo fisso anziché il puntamento con la testa. Ciò consente di estendere il comune modello di interazione [puntamento con la testa e commit](gaze-and-commit.md): 
1. Guarda una destinazione e 
2. Conferma l'intenzione di selezionare tale destinazione effettuando esplicitamente uno degli input secondari seguenti:  
   - Movimento con la mano (ad esempio, una simulazione del tocco)
   - Pressione di un pulsante (ad esempio, su una tastiera Bluetooth o su un dispositivo Clicker)
   - Comando vocale (ad esempio, "Seleziona")
   - Attesa (ovvero l'utente deve semplicemente continuare a guardare la destinazione da selezionare)

Lo sguardo fisso tuttavia ha un comportamento molto diverso da quello del puntamento con la testa da vari punti di vista, pertanto presenta alcune problematiche specifiche. Nelle [linee guida di progettazione per l'uso dello sguardo fisso](eye-tracking.md) vengono riepilogati i vantaggi generali e le problematiche di cui tenere conto quando si usa il tracciamento oculare come input nell'app olografica. In questa sezione vengono trattate le considerazioni relative alla progettazione specifiche per l'uso di _sguardo fisso e commit_.
I nostri occhi prima di tutto si muovono con una rapidità incredibile e quindi sono un mezzo straordinario per individuare velocemente una destinazione all'interno della visualizzazione. Questo rende lo sguardo fisso la soluzione ideale per eseguire rapide azioni di sguardo fisso e commit, soprattutto se combinate con commit rapidi come quelli effettuati tramite simulazione del tocco o pressione di un pulsante.
   
Di seguito verranno fornite le linee guida per la progettazione a cui attenersi quando viene usato lo sguardo fisso per questo tipo di interazione e verranno illustrate le differenze da tenere presenti tra il puntamento con la testa e lo sguardo fisso.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Linee guida di progettazione per sguardo fisso e commit

**Non mostrare un cursore**: se è quasi impossibile interagire senza un cursore quando si usa il puntamento con la testa, il cursore diventa rapidamente un elemento di distrazione e di disturbo quando si usa lo sguardo fisso. Invece di servirti di un cursore per indicare all'utente se il tracciamento oculare funziona e se la destinazione che sta guardando è stata rilevata correttamente, usa evidenziazioni visive non eccessive (altri dettagli vengono forniti più avanti).

**Cercare di fornire un feedback poco invasivo e graduale da visualizzare al passaggio del puntatore**: un feedback visivo ritenuto utile quando si usa il puntamento con la testa può risultare orribile e opprimente quando si usa lo sguardo fisso. Ricorda che i tuoi occhi si muovono molto rapidamente e che si spostano velocemente da un punto all'altro del campo visivo. Rapide e improvvise variazioni dell'evidenziazione (attivata/disattivata) possono produrre un feedback tremolante quando ci si guarda attorno. Pertanto, quando fornisci un feedback da visualizzare al passaggio del puntatore, è consigliabile usare un'evidenziazione graduale, che scompaia altrettanto gradualmente quando si distoglie lo sguardo. Questo significa che all'inizio il feedback sarà appena distinguibile quando si guarda una destinazione. Nel giro di 500-1000 millisecondi l'evidenziazione aumenterà di intensità. Gli utenti alle prime armi potrebbero continuare a guardare la destinazione per essere certi che il sistema l'abbia determinata correttamente, ma gli utenti esperti potrebbero guardare ed eseguire il commit rapidamente senza attendere che il feedback compaia con la massima intensità. È inoltre consigliabile applicare un effetto graduale quando il feedback visualizzato al passaggio del puntatore deve scomparire mediante dissolvenza. Le ricerche svolte hanno dimostrato come le rapide variazioni di movimento e contrasto siano particolarmente rilevabili dalla vista periferica, ovvero nell'area del campo visivo che non si sta guardando.
Non è necessario che l'effetto dissolvenza finale avvenga con la stessa lentezza dell'effetto iniziale di evidenziazione graduale. Questo fattore è fondamentale solo in caso di evidenti variazioni di contrasto o colore per l'evidenziazione. Se il feedback visualizzato al passaggio del puntatore inizialmente ha un carattere piuttosto sottile, è probabile che non si noti alcuna differenza.

**Cercare di ottenere la sincronizzazione dei segnali dello sguardo fisso e del commit**: la sincronizzazione dei segnali di input non è essenziale per un uso di base delle simulazioni del tocco e delle pressioni dei pulsanti. Devi cercare di ottenerla se vuoi usare azioni di commit più complesse che possono comportare lunghi comandi vocali o movimenti della mano complicati. Immagina di guardare una destinazione e di pronunciare un lungo comando vocale. Considerando il tempo che impieghi per pronunciare il comando e il tempo necessario al sistema per rilevare quanto hai detto, intanto lo sguardo in genere si sposta su una nuova destinazione presente nella scena. Pertanto, avvisa gli utenti che potrebbero dover continuare a guardare la destinazione fino al riconoscimento del comando oppure gestisci l'input in modo da determinare l'inizio del comando e l'elemento che l'utente stava guardando.

## <a name="see-also"></a>Vedi anche
* [Interazione basata sullo sguardo] (eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2] (eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
