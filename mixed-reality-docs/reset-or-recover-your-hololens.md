---
title: Reimpostare o ripristinare il HoloLens
description: Istruzioni di base e avanzate per il riavvio o la reimpostazione del HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedura, riavvio, reimpostazione, ripristino, ripristino rigido, ripristino soft, ciclo di alimentazione, HoloLens, arresto
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524038"
---
# <a name="reset-or-recover-your-hololens"></a>Reimpostare o ripristinare il HoloLens

Se si verificano problemi con la HoloLens, è possibile provare a riavviare, reimpostare o addirittura rieseguire il ripristino del dispositivo. In questo documento vengono illustrati i passaggi consigliati per la successione.

## <a name="perform-a-device-reboot"></a>Eseguire un riavvio del dispositivo

Se il HoloLens sta riscontrando problemi o non risponde, provare prima di tutto a riavviarlo tramite uno dei metodi seguenti.

### <a name="perform-a-safe-reboot-via-cortana"></a>Eseguire un riavvio sicuro tramite Cortana

Il modo più sicuro per riavviare il HoloLens è tramite Cortana. Si tratta in genere di un ottimo primo passaggio quando si verifica un problema con HoloLens:
1. Inserire sul dispositivo
2. Verificare che sia acceso, che l'utente sia connesso e che il dispositivo non sia in attesa di una password per sbloccarlo.
3. Pronunciare "Hey Cortana, reboot" o "Hey Cortana, restart".
4. Quando dichiara di confermare la richiesta di conferma. Attendere un secondo per riprodurre un suono dopo che ha terminato la domanda, a indicare che è in ascolto e quindi "Sì".
5. Il dispositivo verrà ora riavviato o riavviato.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Eseguire un riavvio sicuro tramite il portale del dispositivo Windows

Se il precedente non funziona, è possibile provare a riavviare il dispositivo tramite il [portale del dispositivo Windows](using-the-windows-device-portal.md). Nell'angolo superiore destro è disponibile un'opzione per riavviare o arrestare il dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Eseguire un riavvio sicuro tramite il pulsante di alimentazione

Se non si riesce ancora a riavviare il dispositivo, è possibile provare a eseguire un riavvio tramite il pulsante di alimentazione:
1. Premere e tenere premuto il pulsante di alimentazione per 5 secondi
   1. Dopo 1 secondo, si noterà che tutti i 5 LED sono illuminati, quindi si disattiva lentamente da destra a sinistra
   2. Dopo 5 secondi, tutti i LED saranno spenti, a indicare che il comando Shutdown è stato emesso correttamente
   3. Si noti che è importante arrestare la pressione del pulsante immediatamente dopo che tutti i LED sono spenti
2. Attendere 1 minuto per la corretta riuscita dell'arresto. Si noti che l'arresto potrebbe essere ancora in corso anche se gli schermi sono spenti
3. Accendere di nuovo il dispositivo premendo e tenendo premuto il pulsante di alimentazione per 1 secondo

### <a name="perform-an-unsafe-forced-reboot"></a>Eseguire un riavvio forzato non sicuro

Se nessuno dei metodi precedenti riesce a riavviare correttamente il dispositivo, è possibile forzare un riavvio. Si noti che questo metodo equivale a estrarre la batteria dalla HoloLens e, di conseguenza, è un'operazione pericolosa che potrebbe lasciare il dispositivo in uno stato danneggiato. 

>[!WARNING]
>Si tratta di un metodo potenzialmente dannoso e deve essere usato solo nel caso in cui nessuno dei metodi precedenti funzioni.

1. Premere e tenere premuto il pulsante di alimentazione per almeno 10 secondi
   * È bene mantenere il pulsante per più di 10 secondi
   * È possibile ignorare tutte le attività dei LED
2. Rilasciare il pulsante e attendere 2-3 secondi
3. Accendere di nuovo il dispositivo premendo e tenendo premuto il pulsante di alimentazione per 1 secondo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Ripristinare lo stato di pulizia del dispositivo

Se il HoloLens sta ancora riscontrando problemi dopo il riavvio, è possibile provare a reimpostarlo sullo stato Clean Factory. Se si reimposta il dispositivo, verranno cancellati tutti i dati personali, le app e le impostazioni. La reimpostazione installerà solo la versione installata più recente di Windows olografica e sarà necessario ripetere tutti i passaggi di inizializzazione (calibrare, connettersi a Wi-Fi, creare un account utente, scaricare app e così via).
1. Avviare l'app **Impostazioni** ->**Reimposta** **aggiornamento** -> 
2. Selezionare l'opzione **Reimposta dispositivo** e leggere la finestra di dialogo di conferma
3. Se si accetta di reimpostare il dispositivo, il dispositivo viene riavviato e viene visualizzato un set di ingranaggi rotanti con un indicatore di stato
4. Attendere circa 30 minuti per il completamento del processo
5. Il ripristino viene completato e il dispositivo si riavvia nell'esperienza predefinita

## <a name="perform-a-full-device-recovery"></a>Eseguire un ripristino completo del dispositivo

Se, dopo aver eseguito le opzioni precedenti, il dispositivo è **ancora** bloccato, non risponde o si verificano problemi di aggiornamento o software, è possibile ripristinarlo utilizzando lo strumento ripristino dispositivi Windows. Il ripristino del dispositivo è simile alla reimpostazione del dispositivo nel senso che cancellerà tutto il contenuto utente sul dispositivo, tra cui app, giochi, foto, account utente e altro ancora. Se possibile, eseguire il backup di tutte le informazioni che si desidera salvare.

Per ripristinare completamente il HoloLens:
1. Disconnettere tutti i telefoni e i dispositivi Windows dal PC
2. Installare e avviare lo [strumento di ripristino del dispositivo Windows](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) nel PC
3. Connettere la HoloLens al PC usando il cavo micro-USB fornito con
   * Si noti che non tutti i cavi USB vengono creati uguali. Anche se si usa un altro cavo con successo, questo flusso esporrà i nuovi Stati in cui potrebbe non essere possibile eseguire anche il cavo. Quello con cui è stata fornita la HoloLens è l'opzione migliore e più collaudata
4. Se lo strumento rileva automaticamente il dispositivo, verrà visualizzato un riquadro HoloLens. Fare clic su di esso e seguire le istruzioni per completare il processo

>[!NOTE]
>WDRT può ripristinare il dispositivo a una versione precedente di Windows olografico; potrebbe essere necessario installare gli aggiornamenti dopo il lampeggio

Se lo strumento non è in grado di rilevare automaticamente il dispositivo, provare a eseguire le operazioni seguenti:
1. Riavviare il computer e riprovare (questo risolve la maggior parte dei problemi)
2. Fare clic sul **pulsante dispositivo non rilevato**, scegliere **Microsoft HoloLens**e seguire le altre istruzioni visualizzate sullo schermo.
