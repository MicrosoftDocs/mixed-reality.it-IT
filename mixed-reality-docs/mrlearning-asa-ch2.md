---
title: Esercitazioni sugli ancoraggi spaziali di Azure-2. Salvataggio, recupero e condivisione di ancoraggi spaziali di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 4e60ed844e64d736c268dd3ec8453c6c2cb7ad75
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702052"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Salvataggio, recupero e condivisione di ancoraggi spaziali di Azure

In questa esercitazione si apprenderà come salvare i nostri ancoraggi spaziali di Azure tra più sessioni di App salvando le informazioni di ancoraggio nel disco di HoloLens 2. Si apprenderà anche come condividere queste informazioni di ancoraggio ad altri dispositivi per un allineamento di ancoraggio a più dispositivi.

## <a name="objectives"></a>Obiettivi

* Informazioni su come salvare e recuperare le informazioni sull'ancoraggio spaziale di Azure dal disco locale HoloLens 2, per la persistenza tra le sessioni dell'app

* Informazioni su come condividere le informazioni sull'ancoraggio spaziale di Azure tra gli utenti in uno scenario con più dispositivi

## <a name="instructions"></a>Istruzioni

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Mantieni gli ancoraggi di Azure tra le sessioni dell'app-salva l'ID ancoraggio sul disco

1. Cercare e aggiungere la prefabbricazione SaveAnchorToDisk alla scena. Sono inclusi due pulsanti, un pulsante per salvare tutti gli ID di ancoraggio di Azure disponibili sul disco HoloLens 2 e un altro per recuperare gli ID dal disco.

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configurare ciascun pulsante seguendo le istruzioni riportate di seguito

   - Per il pulsante denominato SaveToDisk, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo SaveAzureAnchorIDToDisk () dal componente ASAmoduleScript dell'oggetto ParentAnchor.
   
     > Nota: alcuni pulsanti possono apparire sovrapposti agli altri pulsanti della scena. È possibile modificare il posizionamento del pulsante.

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - Per il pulsante denominato GetFromDisk, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo LoadAzureAnchorIDsFromDisk () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

3. Seguire le istruzioni riportate in Tutoiral 1 per compilare l'applicazione aggiornata nel dispositivo. Dopo aver premuto il pulsante Crea ancoraggio Azure, come è stato fatto nella lezione precedente, è ora possibile salvare l'ID ancoraggio di Azure su disco premendo il pulsante Salva su disco.

4. Riavviare l'applicazione, avviare la sessione di Azure, premere Load Anchor ID, quindi scegliere Individua Azure Anchor per individuare l'ancoraggio associato all'ID salvato sul disco. L'intera scena dovrebbe ora essere posizionata nella posizione in cui è stato salvato in precedenza l'ancoraggio.

### <a name="share-azure-anchors-between-multiple-devices"></a>Condividere gli ancoraggi di Azure tra più dispositivi

Questa sezione illustra come condividere l'ID ancoraggio di Azure tra più dispositivi. Questo consentirà a più dispositivi di eseguire query su Azure per lo stesso ID ancoraggio, consentendo agli ologrammi e alle scene ancorati di essere allineati a livello spaziale. L'allineamento spaziale (visualizzazione degli stessi ologrammi nella stessa posizione fisica tra più dispositivi) è fondamentale per le esperienze condivise locali in HoloLens 2. Esistono diversi modi per trasferire le informazioni relative agli ID di Azure tra i dispositivi, inclusi i metodi descritti nelle esercitazioni delle esperienze condivise degli ancoraggi spaziali di Azure (TODO: Add link). Questo esempio usa un semplice servizio Web per caricare e scaricare gli ID di ancoraggio tra i dispositivi.

1. Aggiungere la prefabbricazione ShareAnchor nella gerarchia. Questa prefabbricata aggiunge due nuovi pulsanti alla scena. uno per il caricamento delle informazioni sull'ID ancoraggio e un altro per il download delle informazioni sull'ID di ancoraggio. 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configurare ciascun pulsante seguendo le istruzioni riportate di seguito

   - Per il pulsante denominato SendSharedAnchor, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo ShareAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - Per il pulsante denominato GetSharedAnchor, creare un nuovo evento sotto il trigger di evento premuto pulsante, nonché il trigger di evento clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo GetSharedAzureAnchor () dal componente ASAmoduleScript dell'oggetto ParentAnchor.

3. Seguire le istruzioni dell' [esercitazione 1](mrlearning-base-ch1.md). per compilare l'applicazione aggiornata nel dispositivo. Dopo aver premuto il pulsante Crea ancoraggio Azure, come è stato fatto nella lezione precedente, è ora possibile condividere l'ID di ancoraggio di Azure con altri dispositivi premendo il pulsante Condividi con altro dispositivo.

   > Nota: Selezionare l'ancoraggio padre e scorrere verso il basso fino allo script di ancoraggio padre. Verificare che il pin di condivisione pubblico sia univoco, in modo che, quando lo si condivide, si sappia che si sta condividendo. Potrebbero essere presenti migliaia di utenti che condividono i propri ancoraggi di Azure. in questo modo sarà possibile assicurarsi di condividere gli ancoraggi di Azure corretti.

4. Se si dispone di un altro dispositivo HoloLens 2, avviare l'applicazione e quindi avviare la sessione di Azure. Premere il pulsante Get Shared Anchor ID, quindi premere il pulsante Locate Azure Anchor per individuare l'ancoraggio associato all'ID salvato sul disco. L'intera scena dovrebbe ora bloccarsi nella posizione, nel punto in cui è stata posizionata sull'altro dispositivo HoloLens 2. Se è presente un solo HoloLens 2, è comunque possibile testare la funzionalità riavviando l'applicazione, avviando la sessione di Azure e quindi premere il pulsante "Ottieni ID ancoraggio condiviso" e quindi fare clic sul pulsante Individua ancoraggio Azure per individuare l'ancoraggio associato al ID salvato sul disco. L'intera scena dovrebbe ora essere posizionata nella posizione in cui è stato salvato in precedenza l'ancoraggio.

## <a name="congratulations"></a>Lezione completata
In questa lezione si è appreso come salvare in modo permanente gli ancoraggi spaziali di Azure tra le sessioni dell'applicazione e i riavvii delle applicazioni salvando l'ID di ancoraggio spaziale di Azure nel disco locale in HoloLens 2. Si è anche appreso come condividere gli ancoraggi spaziali di Azure tra più dispositivi per un'esperienza condivisa di base di un ologramma statico multiutente.

Viene illustrato come implementare gli ancoraggi spaziali di Azure come parte di un'esperienza condivisa locale completamente interattiva durante la lezione finale del modulo sharing. Un'esperienza di condivisione locale può includere funzionalità come la posizione, la rotazione e la scalabilità degli oggetti 3D sincronizzati, gli identificatori per ogni utente e gli Stati delle applicazioni condivise. Gli ancoraggi spaziali di Azure migliorano questi scenari condivisi fornendo a ogni partecipante un ancoraggio comune che consente a tutti gli utenti di visualizzare gli oggetti virtuali nella stessa posizione fisica. Questo vale per un'ampia gamma di piattaforme per dispositivi, inclusi i dispositivi HoloLens, Android e iOS. Per informazioni su come sviluppare un'esperienza condivisa, completare tutte le lezioni del modulo sharing.

Nella lezione successiva verrà illustrato come fornire agli utenti il feedback in tempo reale. Questo feedback includerà informazioni sulla creazione di ancoraggi, sulla qualità della comprensione dell'ambiente e sullo stato della sessione di Azure. Senza commenti, gli utenti potrebbero non sapere se un ancoraggio è stato caricato correttamente in Azure, se la qualità dell'ambiente è sufficiente per la creazione dell'ancoraggio o lo stato corrente.

[Lezione successiva: 3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mrlearning-asa-ch3.md)

