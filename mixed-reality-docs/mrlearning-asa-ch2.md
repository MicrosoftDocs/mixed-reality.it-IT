---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523340"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Il salvataggio, il recupero e la condivisione Anchor spaziale di Azure

In questa esercitazione si apprenderà come salvare i punti di ancoraggio spaziale di Azure tra più sessioni di app salvando le informazioni di ancoraggio su disco della 2 HoloLens. Si apprenderà inoltre a condividere queste informazioni di ancoraggio con gli altri dispositivi per un allineamento di ancoraggio più dispositivi.

## <a name="objectives"></a>Obiettivi

* Informazioni su come salvare e recuperare le informazioni di ancoraggio spaziali Azure dal disco locale 2 HoloLens, per la persistenza tra le sessioni di app

* Informazioni su come condividere le informazioni di ancoraggio spaziali Azure tra gli utenti in uno scenario multi-device

  

## <a name="instructions"></a>Istruzioni

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Rendere persistenti gli ancoraggi Azure tra le sessioni di App - salvare l'ID di ancoraggio su disco

1. Cercare e aggiungere il prefab SaveAnchorToDisk alla scena. Sono inclusi due pulsanti, un pulsante per salvare eventuali ID di ancoraggio di Azure disponibili per il disco 2 HoloLens e l'altro per il recupero di eventuali ID dal disco.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configurare ogni pulsante in base alle istruzioni riportate di seguito
   - Per il pulsante denominato SaveToDisk, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo SaveAzureAnchorIDToDisk() dal componente ASAmoduleScript ParentAnchor dell'oggetto.
   
     > Nota: alcune i pulsanti possono apparire sovrapposti gli altri pulsanti nella scena. È possibile modificare il posizionamento del pulsante.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - Per il pulsante denominato GetFromDisk, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo LoadAzureAnchorIDsFromDisk() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

3. Seguire le istruzioni da 1 Tutoiral per compilare l'applicazione aggiornata al dispositivo. Dopo aver premuto il pulsante di ancoraggio di Azure crea, come è stato fatto nella lezione precedente, è ora possibile salvare l'ID di ancoraggio di Azure per disco premendo di salvataggio al pulsante di disco.

4. Riavviare l'applicazione, avviare la sessione di Azure, premere ID di ancoraggio, carico e quindi premere individuare Azure ancoraggio per individuare il punto di ancoraggio associato con l'ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in corrispondenza della posizione è stato salvato il punto di ancoraggio in precedenza.

### <a name="share-azure-anchors-between-multiple-devices"></a>Condividere punti di ancoraggio di Azure tra più dispositivi

In questa sezione si apprenderà come condividere l'ID di ancoraggio di Azure tra più dispositivi. Questa operazione consentirà di più dispositivi eseguire query di Azure per lo stesso ID di ancoraggio, consentendo la vntana ancorati e scene a livello spaziale da allineare. Allineamento spaziale (vedere il vntana stesso nella stessa posizione fisica tra più dispositivi) è esperienze condivise chiave in locale in 2 HoloLens. Esistono diversi modi per trasferire le informazioni relative alle ID azure tra i dispositivi, inclusi i metodi descritti nelle esperienze condivise Anchor spaziali Azure esercitazioni (TODO: aggiungere un collegamento.) Questo esempio Usa un servizio web semplice per caricare e scaricare gli ID di ancoraggio tra i dispositivi.

1. Aggiungere il prefab ShareAnchor nella gerarchia. Il prefab aggiunge due nuovi pulsanti alla scena; uno per il caricamento di informazioni sull'ID di ancoraggio e l'altro per il download di ancoraggio informazioni relative all'ID. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configurare ogni pulsante in base alle istruzioni riportate di seguito

   - Per il pulsante denominato, SendSharedAnchor, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo ShareAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - Per il pulsante denominato, GetSharedAnchor, creare un nuovo evento sotto il trigger di evento fatto clic sul pulsante, nonché il trigger di evento nel fare clic su. Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo GetSharedAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

3. Seguire le istruzioni da [esercitazione 1](mrlearning-base-ch1.md). Per compilare l'applicazione aggiornata al dispositivo. Dopo aver premuto il pulsante di ancoraggio di Azure crea, come è stato fatto nella lezione precedente, è possibile ora condividere l'ID di ancoraggio di Azure ad altri dispositivi facendo clic sul pulsante di condivisione per altri dispositivi.

   > Nota: Selezionare l'ancoraggio padre e scorrere verso il basso lo script di ancoraggio padre. Assicurarsi che il pin di condivisione pubblico sia univoco, in modo che quando si condivide, si conosce che l'indirizzo sia tuo che si desidera condividere. Potrebbe essere presenti migliaia di utenti che condividono i punti di ancoraggio Azure, in modo che questa operazione consentirà di verificare che si desidera condividere i punti di ancoraggio Azure corretti.

4. Se si dispone di un altro dispositivo HoloLens 2, avviare l'applicazione e quindi avviare la sessione di Azure. Fare clic sul pulsante Ottieni ID di ancoraggio condiviso e quindi premere il pulsante di ancoraggio di Azure individuare per individuare il punto di ancoraggio associato con l'ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in where è stata posizionata nell'altro dispositivo HoloLens 2. Se è solo uno 2 HoloLens, si potrebbe comunque testare la funzionalità, riavviare l'applicazione, avvio della sessione di Azure e quindi fare clic sul pulsante "Get Shared ancoraggio ID" pulsante e quindi premere il pulsante di ancoraggio di Azure individuare per individuare il punto di ancoraggio associato il ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in corrispondenza della posizione è stato salvato il punto di ancoraggio in precedenza.

## <a name="congratulations"></a>Lezione completata
In questa lezione è stato descritto rendere persistenti gli ancoraggi spaziali Azure tra le sessioni delle applicazioni e i riavvii dell'applicazione dal salvataggio dell'ID di ancoraggio spaziale di Azure nel disco locale in HoloLens 2. Inoltre appreso come condividere gli ancoraggi spaziali Azure tra più dispositivi per un'esperienza di base ologrammi multiutente, statici condivisi.

Abbiamo informazioni su come implementare gli ancoraggi spaziale di Azure come parte di un'esperienza condivisa locale completamente interattiva durante la lezione finale del modulo di condivisione. Un'esperienza di condivisione locale può includere funzionalità, ad esempio identificatori oggetto 3D sincronizzato di posizione, rotazione e scalabilità, per ogni utente e condivisi stati dell'applicazione. Azure Anchor spaziali migliora questi scenari condivisi, fornendo ogni partecipante con un ancoraggio comune che consente a tutti gli utenti di visualizzare gli oggetti virtuali nella stessa posizione fisica. Questo vale per una gamma di piattaforme del dispositivo, inclusi i dispositivi HoloLens, Android e iOS. Per informazioni su come sviluppare un'esperienza condivisa, completare tutte le lezioni del modulo di condivisione.

Nella lezione successiva si apprenderà come fornire agli utenti con il feedback in tempo reale. Questi commenti e suggerimenti verranno incluse informazioni sull'ancoraggio la creazione, la qualità della conoscenza di ambiente e lo stato della sessione di Azure. Senza commenti e suggerimenti, agli utenti potrebbero non sapere se un ancoraggio è stato completato il caricamento in Azure, se la qualità dell'ambiente è sufficiente per la creazione di ancoraggio o lo stato corrente.

[Lezione successiva: ASA Tutorial 3](mrlearning-asa-ch3.md)

