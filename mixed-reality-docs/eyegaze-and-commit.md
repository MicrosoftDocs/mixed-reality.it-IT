---
title: Visiva e commit
description: Panoramica del modello di input visiva e commit
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Rilevamento rossi, mista realtà, Input, sguardo sotto controllo, come destinazione rossi, HoloLens 2, selezione basata su sotto controllo
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66455087"
---
# <a name="eye-gaze-and-commit"></a>Visiva e commit
Con 2 HoloLens, abbiamo la straordinaria opportunità per rendere sguardo & commit più veloce e più a proprio agio usando occhio sguardo anziché sguardo head. Ciò consente di estendere i comuni [head sguardo ed eseguire il commit](gaze-and-commit.md) modello di interazione: 
1. È sufficiente esaminare una destinazione e 
2. Per confermare l'intenzione di selezionare la destinazione, eseguire un database secondario con esplicito di input, ad esempio r:  
   - Movimento mano (ad esempio, un aereo toccare)
   - Fare clic sul pulsante (ad esempio, su una tastiera Bluetooth o clicker)
   - Esprimere il comando (ad esempio, "Select")
   - Appartamento (ad esempio, l'utente mantiene analizzando semplicemente selezionare la destinazione)

Tuttavia, sguardo occhio si comporta in modo molto diverso da sguardo head in determinati modi e pertanto viene fornito con una serie di difficoltà univoco. Nel [occhio estasiati Design Guidelines](eye-tracking.md), riepilogheremo generali vantaggi e problematiche da prendere in considerazione quando si usa dell'occhio rilevamento come input per l'app holographic. In questa sezione presenteremo le considerazioni di progettazione specifiche per visiva & commit.
Prima di tutto gli occhi spostare incredibilmente veloce e sono quindi ideali in rapidamente come destinazione attraverso la vista. Ciò rende occhio estasiati ideale per azioni rapide sguardo e commit soprattutto se combinate con commit veloce, ad esempio una macchina-indice puntato o un pulsante.
   
Nell'esempio seguente, si risolverà linee guida di progettazione quando si utilizzano occhio estasiati per questo tipo di interazione e verranno illustrate le differenze tra sguardo head e occhio è necessario tenere in considerazione.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Linee guida per visiva e il commit di progettazione

**Non visualizzare un cursore**: Mentre è quasi impossibile interagire senza un cursore quando si usa head estasiati, il cursore diventa rapidamente rappresentano una distrazione e indesiderate quando si usa sguardo sotto controllo. Anziché basarsi su un cursore per informare l'utente se occhio rilevamento funziona e ha corretto ha rilevato l'attualmente cercato nella destinazione, usare meno evidenti visual Evidenzia (ulteriori dettagli sotto).

**Cercano di ottenere commenti e suggerimenti al passaggio del mouse combinata sottili**: Che cosa sembra eccezionale indicazioni visive per sguardo head può comportare esperienze terribile, piuttosto complessa usando sguardo sotto controllo. Tenere presente che gli occhi sono molto veloci, darting rapidamente tra i punti del campo di visualizzazione. Modifiche di evidenziazione improvvisi rapida (attivato/disattivato) possono comportare flickery commenti e suggerimenti durante la ricerca. Pertanto, quando si forniscono commenti e suggerimenti al passaggio del mouse, è consigliabile con un'evidenziazione in modo uniforme devono essere smussati aggiuntivo (e devono essere smussati-out durante la ricerca da subito). Ciò significa che inizialmente è poco notare i commenti e suggerimenti quando si esamina una destinazione. Nel corso di 500 e 1000 ms aumenterebbe di intensità di evidenziazione. Mentre gli utenti meno esperti potrebbero mantenere esamina la destinazione per assicurarsi che il sistema ha determinato correttamente che la destinazione con lo stato attivo, può rapidamente estasiati & commit viene eseguito senza attendere il feedback è la massima intensità da utenti esperti. Inoltre, è anche consigliabile usare una sfumatura orizzontale quando dissolvenza in uscita i commenti e suggerimenti al passaggio del mouse. Research ha dimostrato che modifiche di movimento e contrasto rapide sono molto evidenti nella tua vision periferiche (questa operazione, l'area del campo visivo in cui non è indispensabile). La dissolvenza privo di lentezza del blend aggiuntivo. Questo è fondamentale solo quando è disponibile a contrasto elevato o modifiche ai colori per l'evidenziazione. Se i commenti e suggerimenti al passaggio del mouse è stato alquanto impercettibile per iniziare, probabilmente non si verificherà una differenza.

**Cercare la sincronizzazione dei segnali sguardo e commit**: La sincronizzazione di input segnali possono essere meno difficile per semplice sguardo & commit, pertanto, non preoccuparti! È un elemento da cercare nel caso in cui si desidera usare azioni commit più complicate, ma che può comportare movimenti della mano complesse o i comandi vocali lunghi. Si supponga Esaminiamo target e utter un comando vocali lunghi. Presa in considerazione l'ora in cui è necessario parlare e l'ora in cui il sistema è necessaria per determinare cosa hai detto, lo sguardo occhio in genere tempo passa all'alcuni nuova destinazione nella scena. Di conseguenza, rendere gli utenti consapevoli che possono dover mantenere esaminando una destinazione fino a quando non è stato riconosciuto il comando o gestire l'input in un modo per determinare che genera del comando e ciò che l'utente era stata esaminando epoca.

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Movimenti della mano](gestures.md)
* [Input vocale](voice-design.md)
* [Controller del movimento](motion-controllers.md)
