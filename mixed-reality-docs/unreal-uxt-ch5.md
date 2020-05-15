---
title: 5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi
description: Parte 5 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840400"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Aggiunta di un pulsante e ripristino delle posizioni dei pezzi

In questa sezione si continua a illustrare le funzionalità del plug-in Mixed Reality Toolkit UX Tools e a creare le funzionalità dell'app di scacchi. Si creerà una nuova funzione e si imparerà a trasferire i riferimenti agli attori dal proprio livello a un progetto.

## <a name="objectives"></a>Obiettivi

* Aggiungere un pulsante a un progetto
* Creare una nuova funzione "Reset Location" (Ripristina posizione) che ripristina la posizione originale di un pezzo
* Associare il pulsante in modo che attivi la funzione appena creata quando viene premuto

## <a name="create-a-function-to-reset-location"></a>Creare una funzione per ripristinare la posizione

1.  Apri **WhiteKing**. Nel pannello **My Blueprint** (Progetto personale) fai clic sul pulsante "+" accanto alla sezione **Functions** (Funzioni) per creare una nuova funzione. Assegna alla funzione il nome "Reset Location" (Ripristina posizione). 

2.  Nel progetto **Reset Location** (Ripristina posizione) appena creato, trascina il pin di esecuzione e rilascialo in un punto qualsiasi della griglia del progetto per chiamare un nodo **SetActorRelativeTransform**. Questa funzione imposta la trasformazione (posizione, rotazione e scala) di un attore rispetto al relativo elemento padre. Questa funzione verrà usata per ripristinare la posizione del Re sulla scacchiera, anche se è stata spostata dalla posizione originale. Crea un nodo **Make Transform** (Esegui trasformazione) nella posizione X = -26, Y = 4, Z = 0 e collegalo all'input New Relative Transform (Nuova trasformazione relativa). 

![Funzione di ripristino della posizione](images/unreal-uxt/5-function.PNG)

3.  Compila e salva **WhiteKing**. Torna alla finestra principale. 

## <a name="add-a-button"></a>Aggiungere un pulsante

1.  Nella cartella **Blueprints** (Progetti) crea un nuovo progetto che costituisca una sottoclasse di SimpleButton. SimpleButton è un Blueprint Actor (attore di progetto) di un pulsante 3D fornito con il plug-in UX Tools. Assegna al pulsante il nome "ResetButton" e fai doppio clic per aprire il progetto. 

![Creare il nuovo progetto come sottoclasse di SimpleButton](images/unreal-uxt/5-subclass.PNG)

2.  Nel pannello **Components** (Componenti ) fai clic su **PressableButton (Inherited)** (PressableButton - Ereditato). Nel pannello dei dettagli scorri fino alla sezione **Events** (Eventi). Fai clic sul pulsante con il segno più verde accanto a **On Button Pressed** (Alla pressione del pulsante). In questo modo, verrà aggiunto un evento **On Button Pressed** (Alla pressione del pulsante) al grafico degli eventi, che verrà chiamato ogni volta che viene premuto il pulsante. Da qui è possibile chiamare la funzione di ripristino della posizione di WhiteKing. A questo scopo, sarà prima necessario ottenere un riferimento all'attore WhiteKing nel livello in uso. 

3.  Nel pannello **My Blueprint** (Progetto personale), trova la sezione **Variables** (Variabili) e fai clic sul pulsante **+** per aggiungere una nuova variabile. Assegna alla variabile il nome "WhiteKing". Nel pannello dei dettagli seleziona l'elenco a discesa accanto a **Variable Type** (Tipo di variabile), cerca "WhiteKing" e seleziona **Object Reference** (Riferimento oggetto). Seleziona infine la casella accanto a **Instance Editable** (Istanza modificabile). In questo modo la variabile potrà essere impostata dal livello principale. 

![Creazione di una variabile](images/unreal-uxt/5-var.PNG)

4.  Trascina la variabile WhiteKing da **My Blueprint > Variables** (Progetto personale > Variabile) in Simple Button Event Graph (Grafico eventi SimpleButton). Scegli **Get WhiteKing** (Ottieni WhiteKing). 

5.  Trascina il pin di output di WhiteKing e rilascialo per inserire un nuovo nodo. Seleziona la funzione **Reset Location** (Ripristina posizione). Trascina infine il pin di esecuzione in uscita da **On Button Pressed** (Alla pressione del pulsante) al pin di esecuzione in ingresso in **Reset Location** (Ripristina posizione). Fai clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto ResetButton e quindi torna alla finestra principale. 

![Chiamata della funzione di ripristino della posizione alla pressione del pulsante](images/unreal-uxt/5-callresetloc.PNG)

6.  Trascina **SimpleButton** nel viewport e impostane la posizione su X = 50, Y =-25, Z = 10. In **Default** (Valore predefinito) imposta il valore della variabile WhiteKing su **WhiteKing**.

![Impostazione della variabile](images/unreal-uxt/5-buttonlevel.PNG)

Disponi ora di un'app di realtà mista con un pezzo degli scacchi afferrabile e una scacchiera, nonché un pulsante completamente funzionante che, quando viene premuto, ripristina la posizione del pezzo. L'app completata fino a questo punto è disponibile in [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). Al termine di questa esercitazione, è possibile andare avanti e configurare gli altri pezzi degli scacchi, in modo che venga ripristinata l'intera scacchiera quando l'utente preme il pulsante.

![Schermata finale in viewport](images/unreal-uxt/5-endscene.PNG)

[Sezione successiva: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore](unreal-uxt-ch6.md)