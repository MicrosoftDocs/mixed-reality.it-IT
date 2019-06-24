---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327454"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a>Persistenza e la condivisione dei punti di ancoraggio spaziali Azure

In questa lezione si apprenderà come rendere permanente nostro Anchor spaziali Azure tra più sessioni di app tramite il salvataggio le informazioni di ancoraggio su disco della 2 HoloLens. Si apprenderà inoltre a condividere queste informazioni di ancoraggio con gli altri dispositivi per un allineamento di ancoraggio più dispositivi.

## <a name="objectives"></a>Obiettivi

* Informazioni su come salvare e recuperare le informazioni di ancoraggio spaziali Azure dal disco locale 2 HoloLens, per la persistenza tra le sessioni di app

* Informazioni su come condividere le informazioni di ancoraggio spaziali Azure tra gli utenti in uno scenario multi-device

  

## <a name="instructions"></a>Istruzioni

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Rendere persistenti gli ancoraggi Azure tra le sessioni di App - salvare l'ID di ancoraggio su disco

1. Cercare e aggiungere il prefab "SaveAnchorToDisk" alla scena. Sono inclusi due pulsanti, un pulsante per salvare eventuali ID di ancoraggio di Azure disponibili per il disco 2 HoloLens e l'altro per il recupero di eventuali ID dal disco.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configurare ogni pulsante in base alle istruzioni riportate di seguito
   - Per il pulsante denominato "SaveToDisk", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo SaveAzureAnchorIDToDisk() dal componente ASAmoduleScript ParentAnchor dell'oggetto.
   
     > Nota: alcune i pulsanti possono apparire sovrapposti gli altri pulsanti nella scena. È possibile modificare il posizionamento del pulsante.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - Per il pulsante denominato "GetFromDisk", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo LoadAzureAnchorIDsFromDisk() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

3. Seguire le istruzioni della lezione 1 per compilare l'applicazione aggiornata al dispositivo. Dopo aver premuto il pulsante "Create Azure ancoraggio", come è stato fatto nella lezione precedente, è ora possibile salvare l'ID di ancoraggio di Azure per disco premendo di salvataggio al pulsante di disco.

4. Riavviare l'applicazione, avviare la sessione di Azure, fare clic sul pulsante "ID carico ancoraggio" e quindi fare clic sul pulsante "Ancoraggio di Azure individuare" per individuare il punto di ancoraggio associato con l'ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in corrispondenza della posizione è stato salvato il punto di ancoraggio in precedenza.

### <a name="share-azure-anchors-between-multiple-devices"></a>Condividere punti di ancoraggio di Azure tra più dispositivi

In questa sezione si apprenderà come condividere l'ID di ancoraggio di Azure tra più dispositivi. Questa operazione consentirà di più dispositivi eseguire query di Azure per lo stesso ID di ancoraggio, consentendo la vntana ancorati e scene a livello spaziale da allineare. Allineamento spaziale (vedere il vntana stesso nella stessa posizione fisica tra più dispositivi) è esperienze condivise chiave in locale in 2 HoloLens. Esistono diversi modi per trasferire le informazioni relative alle ID azure tra i dispositivi, inclusi i metodi descritti nelle esperienze condivise Anchor spaziali Azure esercitazioni (TODO: aggiungere un collegamento.) Questo esempio Usa un servizio web semplice per caricare e scaricare gli ID di ancoraggio tra i dispositivi.

1. Aggiungere il prefab "ShareAnchor" nella gerarchia. Il prefab aggiunge due nuovi pulsanti alla scena; uno per il caricamento di informazioni sull'ID di ancoraggio e l'altro per il download di ancoraggio informazioni relative all'ID. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configurare ogni pulsante in base alle istruzioni riportate di seguito

   - Per il pulsante denominato "SendSharedAnchor", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo ShareAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - Per il pulsante denominato "GetSharedAnchor", creare un nuovo evento sotto il trigger di evento "Pulsante premuto" così come il trigger di evento "Scegliere". Trascinare l'oggetto ParentAnchor nel campo vuoto e assegnare il metodo GetSharedAzureAnchor() dal componente ASAmoduleScript ParentAnchor dell'oggetto.

3. Seguire le istruzioni da [lezione 1](mrlearning-base-ch1.md). Per compilare l'applicazione aggiornata al dispositivo. Dopo aver premuto il pulsante "Create Azure ancoraggio", come è stato fatto nella lezione precedente, è possibile ora condividere l'ID di ancoraggio di Azure ad altri dispositivi facendo clic sul pulsante di condivisione per altri dispositivi.

   > Nota: Selezionare l'ancoraggio padre e scorrere verso il basso lo script di ancoraggio padre. Assicurarsi che il "Aggiungi condivisione pubblica" sia univoco, in modo che quando si condivide, si conosce che l'indirizzo sia tuo che si desidera condividere. Potrebbe essere presenti migliaia di utenti che condividono i punti di ancoraggio di Azure, in modo che questa operazione consentirà di verificare che si condivide gli ancoraggi Azure corretto.

4. Se si dispone di un altro dispositivo HoloLens 2, avviare l'applicazione e quindi avviare la sessione di Azure. Fare clic sul pulsante "Get Shared ancoraggio ID" e quindi fare clic sul pulsante "Ancoraggio di Azure individuare" per individuare il punto di ancoraggio associato con l'ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in where è stata posizionata nell'altro dispositivo HoloLens 2. Se si ha solo 2 HoloLens uno, si potrebbe comunque testare la funzionalità, riavviare l'applicazione, avvio della sessione di Azure e quindi fare clic sul pulsante "Get Shared ancoraggio ID" pulsante e quindi fare clic sul pulsante "Ancoraggio di Azure individuare" per individuare il punto di ancoraggio associato l'ID è stato salvato sul disco. L'intera scena a questo punto deve essere bloccato in posizione, in corrispondenza della posizione è stato salvato il punto di ancoraggio in precedenza.

## <a name="congratulations"></a>Lezione completata
In questa lezione è stato descritto come salvare in modo permanente gli ancoraggi spaziale di Azure tra le sessioni di app e i riavvii dell'app dal salvataggio dell'ID di ancoraggio spaziale di Azure nel disco locale di 2 HoloLens. Inoltre appreso come condividere gli ancoraggi spaziali Azure tra più dispositivi per un'esperienza di base ologrammi multiutente, statici condivisi!

Si apprenderà come implementare gli ancoraggi spaziale di Azure come parte di un'esperienza condivisa locale completamente interattiva durante la lezione finale del modulo di condivisione. Un'esperienza di condivisione locale può includere funzionalità, ad esempio identificatori oggetto 3D sincronizzato di posizione, rotazione e scalabilità, per ogni utente e condivisi stati dell'applicazione. Azure Anchor spaziali migliora questi scenari condivisi, fornendo ogni partecipante con un punto di ancoraggio comune che tutti gli utenti possono visualizzare gli oggetti virtuali nella stessa posizione fisica. Questo vale per una gamma di piattaforme del dispositivo, inclusi i dispositivi HoloLens, Android e iOS. Per informazioni su come sviluppare un'esperienza condivisa, completare tutte le lezioni del modulo di condivisione.

Nella lezione successiva si apprenderà come fornire agli utenti con il feedback in tempo reale. Questi commenti e suggerimenti verranno incluse informazioni sull'ancoraggio la creazione, la qualità della conoscenza di ambiente e lo stato della sessione di Azure. Senza commenti e suggerimenti, agli utenti potrebbero non sapere se un ancoraggio è stato completato il caricamento in Azure, se la qualità dell'ambiente è sufficiente per la creazione di ancoraggio o lo stato corrente.

[Lezione successiva: ASA lezione 3](mrlearning-asa-ch3.md)

