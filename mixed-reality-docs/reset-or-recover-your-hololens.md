---
title: Reimpostare o il ripristino di HoloLens
description: Istruzioni di base e avanzate per il riavvio o la reimpostazione di HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedure, riavviare, reimpostare, ripristino, reimpostazione hardware, reimpostare il software, ciclo di alimentazione, HoloLens, arresto
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599882"
---
# <a name="reset-or-recover-your-hololens"></a>Reimpostare o il ripristino di HoloLens

Se sono stati riscontrati problemi con i HoloLens è possibile provare a riavviare il computer, reimpostare o persino con ripristino di un dispositivo flash nuovamente. Questo documento verrà consentono di eseguire le procedure consigliate in successione.

## <a name="perform-a-device-reboot"></a>Eseguire un riavvio del dispositivo

Se il HoloLens sta riscontrando problemi o non risponde, innanzitutto provare a riavviare, tramite uno dei metodi seguenti.

### <a name="perform-a-safe-reboot-via-cortana"></a>Eseguire un riavvio sicuro tramite Cortana

Il modo più sicuro il riavvio di HoloLens è tramite Cortana. Ciò è in genere un notevole passo prima quando si verifica un problema con HoloLens:
1. Inserire nel dispositivo
2. Assicurarsi che l'accensione e un utente è connesso il dispositivo non è in attesa di una password per sbloccarlo.
3. Pronunciare "Ehi Cortana, riavviare" o "Ehi Cortana, riavviare."
4. Quando Anna riconosce Anna verrà chiesto di confermare l'operazione. Attendere un secondo per un suono da riprodurre dopo che Anna ha terminato la domanda, che indica che è in ascolto all'utente e quindi pronunciare "Sì".
5. Il dispositivo verrà ora riavvio/riavvio.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Eseguire un riavvio sicuro tramite Windows Device Portal

Se il codice precedente non funziona, è possibile provare a riavviare il dispositivo tramite [Windows Device Portal](using-the-windows-device-portal.md). In alto a destra, è disponibile un'opzione di arresto/riavvio del dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Eseguire un riavvio sicuro tramite il pulsante di alimentazione

Se è ancora non è possibile riavviare il dispositivo, è possibile provare a eseguire un riavvio tramite il pulsante di alimentazione:
1. Premere e tenere premuto il pulsante di alimentazione per 5 secondi
   1. Dopo 1 secondo, si visualizzeranno tutti illuminano LED 5, quindi lentamente disattivare da destra a sinistra
   2. Dopo 5 secondi, tutti i LED è disattivata, che indica che il comando di arresto è stato rilasciato correttamente
   3. Si noti che è importante arrestare premendo il pulsante immediatamente dopo tutti i LED di sono disattivato
2. Attendere 1 minuto per l'arresto normalmente abbia esito positivo. Si noti che l'arresto potrebbe essere ancora in corso anche se le visualizzazioni sono disattivate
3. Accendere il dispositivo nuovamente tenendo premuto il pulsante di alimentazione per 1 secondo

### <a name="perform-an-unsafe-forced-reboot"></a>Eseguire un riavvio forzato unsafe

Se nessuno dei suddetti metodi sono in grado di riavviare correttamente il dispositivo, è possibile forzare un riavvio. Si noti che questo metodo equivale a eseguire il pull della batteria da di HoloLens e di conseguenza, è un'operazione pericolosa potrebbe lasciare il dispositivo in uno stato danneggiato. 

>[!WARNING]
>Questo è un metodo potenzialmente dannoso e deve essere usato solo nel caso in cui nessuno dei suddetti metodi di lavoro.

1. Premere e tenere premuto il pulsante di alimentazione per almeno 10 secondi
   * È possibile tenere premuto il pulsante per più di 10 secondi
   * È possibile ignorare qualsiasi attività del LED
2. Rilasciare il pulsante e attendere 2-3 secondi
3. Accendere il dispositivo nuovamente tenendo premuto il pulsante di alimentazione per 1 secondo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Ripristinare uno stato pulito del produttore del dispositivo

Se il HoloLens è continuano a verificarsi problemi dopo il riavvio, è possibile ripristinarne lo stato originario factory. Se si reimposta il dispositivo, verranno cancellate tutti i dati personali, App e impostazioni. La reimpostazione verrà installato solo l'ultima versione installata di Windows Holographic e sarà necessario eseguire il rollforward di tutti i passaggi di inizializzazione (calibrare, connettersi al Wi-Fi, creare un account utente, scaricare le App e così via...).
1. Avviare il **le impostazioni** -> app **Update** -> **reimpostare**
2. Selezionare il **dispositivo ripristinato alle impostazioni** opzione e la finestra di dialogo di conferma di lettura
3. Se si accettano i reimpostare il dispositivo, il dispositivo verrà riavviato e di rotazione gears con un indicatore di stato visualizzati
4. Attendere circa 30 minuti completare questo processo
5. La reimpostazione verrà completata e il dispositivo verrà riavviato con l'uscita dell'esperienza di finestra

## <a name="perform-a-full-device-recovery"></a>Eseguire un ripristino del dispositivo completa

Se, dopo aver eseguito le opzioni precedenti, la periferica **comunque** bloccata, non risponde o che sta rilevando problemi software o aggiornamenti è possibile ripristinare tramite il Windows Device Recovery Tool. Il ripristino del dispositivo è simile a reimpostarlo nel senso che verranno cancellati tutti i contenuti di utente nel dispositivo, inclusi App, giochi, foto, gli account utente e altro ancora. Se possibile, le informazioni che si desidera mantenere il backup.

Per un ripristino completo di HoloLens:
1. Scollegare tutti i telefoni e dispositivi di Windows dal computer
2. Installare e avviare il [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) nel PC
3. Connettere il HoloLens al PC usando il cavo micro-USB fornito con
   * Si noti che non tutti i cavi USB sono uguali. Anche se è stato usato un altro cavo correttamente, questo flusso esporrà nuovi Stati in cui il cavo potrebbe non essere ottimali. Quello di HoloLens integrava è l'opzione migliore e più ben collaudata
4. Se lo strumento rileva automaticamente il dispositivo verrà visualizzato un riquadro HoloLens. Clic su di esso e seguire le istruzioni per completare il processo

>[!NOTE]
>WDRT potrebbe eseguire il ripristino del dispositivo per una versione precedente di Windows Holographic; potrebbe essere necessario installare gli aggiornamenti dopo il lampeggiamento

Se lo strumento è in grado di rilevare automaticamente il dispositivo, procedere come segue:
1. Riavviare il PC e provare di nuovo (questa correzione risolve la maggior parte dei problemi)
2. Scegliere il **il dispositivo non è stato rilevato sul pulsante**, scegliere **Microsoft HoloLens**e seguire le istruzioni sullo schermo
