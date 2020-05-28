---
title: Interazione basata su sguardo fisso
description: HoloLens 2 consente di raggiungere un nuovo livello di comprensione contestuale e umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative a cosa gli utenti stanno guardando. Questa pagina descrive le raccomandazioni di progettazione per gli sviluppatori che vogliono usare gli sguardi come input.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Rilevamento degli occhi, realtà mista, input, sguardi occhi
ms.openlocfilehash: 2ae7723f116771986edc757f1c9d4f454b0a256f
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111032"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interazione basata sugli sguardi su HoloLens 2

![Demo sul rilevamento degli occhi in MRTK](images/mrtk_et_scenemenu.jpg)

Una delle nuove interessanti funzionalità di HoloLens 2 è la verifica degli occhi.
Nella pagina [HoloLens 2](eye-tracking.md) è stata illustrata la necessità di ogni utente di eseguire una [calibrazione](https://docs.microsoft.com/hololens/hololens-calibration), purché siano disponibili istruzioni per gli sviluppatori e casi di utilizzo evidenziati per la verifica degli occhi.
L'input con sguardo oculare è ancora un tipo di input utente piuttosto nuovo ed è molto interessante da imparare. Anche se l'input degli sguardi è usato in modo molto sottile nell'esperienza della shell olografica (l'interfaccia utente visualizzata quando si avvia HoloLens 2), più app, ad esempio ["HoloLens Playground"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), illustrano esempi eccezionali su come l'input di sguardi occhi possa aggiungere la magia dell'esperienza olografica.
In questa pagina vengono illustrate le considerazioni di progettazione per l'integrazione dell'input Eye-sguardi per interagire con le applicazioni olografiche.
Verranno fornite informazioni sui vantaggi principali, oltre a una sfida univoca in grado di ottenere un input mirato.  
In base a questi, sono disponibili diversi consigli per la progettazione che consentono di creare interfacce utente supportate da sguardi oculisti. 

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Sguardo attento</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Linee guida per la progettazione di input con sguardo attento
La creazione di un'interazione che sfrutta la scelta rapida per gli occhi in rapida evoluzione può risultare complessa. In questa sezione vengono riepilogati i vantaggi e le questioni principali da considerare durante la progettazione dell'applicazione. 

### <a name="benefits-of-eye-gaze-input"></a>Vantaggi dell'input con sguardo a occhio
- **Puntamento ad alta velocità.** Il muscolo occhi è il muscolo più veloce nel corpo umano. 

- **Sforzo limitato.** Non sono quasi necessari movimenti fisici. 

- **Natura implicita.** Spesso descritta dagli utenti come "lettura mentale", le informazioni sui movimenti degli occhi di un utente consentono al sistema di sapere quale destinazione prevede l'intervento dell'utente. 

- **Canale di input alternativo.** Eye-sguardi può offrire un potente input di supporto per l'input vocale e di mano che si basa su anni di esperienza degli utenti in base al coordinamento degli occhi.

- **Attenzione visiva.** Un altro vantaggio importante è la possibilità di dedurre ciò a cui un utente presta attenzione. Questo può essere utile in diverse aree applicative, da valutare in modo più efficace le diverse progettazioni per aiutare le interfacce utente più intelligenti e suggerimenti sociali avanzati per la comunicazione remota.

In breve, l'uso di Eye-sguardi come input offre un segnale di input contestuale rapido e semplice. Questa operazione è particolarmente efficace se combinata con altri input, ad esempio input *vocale* e *manuale* , per confermare la finalità dell'utente.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Problemi di Eye-sguardi come input
Grazie a un elevato consumo di energia, è molto responsabile.
Sebbene sia possibile usare gli sguardi per creare esperienze utente soddisfacenti, che rendono un supereroe, è anche importante sapere che cosa non è adatto a tenere in considerazione questo aspetto. Di seguito sono illustrate alcune delle *questioni* da prendere in considerazione e il modo in cui risolverle quando si lavora con l'input Eye-sguardi: 

- **Il controllo degli sguardi è "always on"** Nel momento in cui si aprono i coperchi degli occhi, gli occhi iniziano a fissando su elementi nell'ambiente. Reagire a ogni aspetto effettuato e rilasciare accidentalmente le azioni, perché si è verificato un problema troppo lungo, comporterebbe un'esperienza insoddisfacente.
È quindi consigliabile combinare gli occhi con un *comando vocale*, un *gesto della mano*, un *clic su un pulsante* o un'abitazione estesa per attivare la selezione di una destinazione (per altre informazioni, vedere [Eye-sguardi e commit](gaze-and-commit-eyes.md)).
Questa soluzione consente anche una modalità in cui l'utente può esaminarsi liberamente senza essere sopraffatto dall'attivazione involontaria di qualcosa. Questo problema deve essere preso in considerazione anche quando si progettano commenti visivi e uditivi quando si esamina una destinazione.
Provare a non sovraccaricare l'utente con effetti di pop-out immediati o rumori al passaggio del mouse. La sottigliezza è Key. Verranno illustrate alcune procedure consigliate per questo più avanti quando si parlano le [raccomandazioni di progettazione](eye-gaze-interaction.md#design-recommendations).

- **Confronto tra osservazione e controllo** Si supponga di voler raddrizzare con precisione una fotografia sulla parete. Guardi pertanto i bordi e l'area circostante per verificare che l'immagine sia allineata correttamente. A questo punto, si supponga di voler usare il proprio sguardo come input per spostare l'immagine. L'esecuzione diventa veramente difficoltosa. Viene descritto il doppio ruolo di occhio quando è necessario sia per l'input che per il controllo. 

- **Lasciare prima di fare clic su:** Per le selezioni di destinazione rapide, la ricerca ha dimostrato che lo sguardo a un utente può andare avanti prima di concludere un clic manuale (ad esempio, un rubinetto d'aria). Di conseguenza, è necessario prestare particolare attenzione alla sincronizzazione del segnale di sguardo rapido con un input di controllo più lento (ad esempio, Voice, Hands, controller).

- **Destinazioni di piccole dimensioni:** Si conosce la sensazione quando si tenta di leggere il testo che è troppo piccolo per leggere comodamente? Questa sensazione di limitazione degli sguardi può comportare la disattivazione e l'esaurimento, perché si tenta di modificare gli occhi per concentrarsi meglio.
Si tratta di un sentimento che è possibile richiamare negli utenti quando si impone loro di selezionare destinazioni troppo piccole nell'applicazione usando la destinazione degli occhi.
Durante la progettazione, per creare un'esperienza piacevole e confortevole per gli utenti, è consigliabile definire destinazioni con un angolo visivo di almeno 2 gradi.

- **Spostamenti occhi** incompleti Gli occhi eseguono movimenti rapidi dalla fissa alla fissa. Se guardi i percorsi di analisi dei movimenti oculari registrati, noterai che risultano irregolari. Gli occhi si spostano rapidamente e in salti spontanei rispetto ai movimenti a *capo* o a *mano*.  

- **Verifica dell'affidabilità:** L'accuratezza del rilevamento degli sguardi può compromettere leggermente la luce quando gli occhi si adattano alle nuove condizioni.
Sebbene questo non debba necessariamente influire sulla progettazione dell'applicazione, in quanto l'accuratezza dovrebbe essere compresa nel limite di 2 °, potrebbe essere necessario che l'utente ricalibra nuovamente. 


## <a name="design-recommendations"></a>Suggerimenti per la progettazione
Di seguito è riportato un elenco di raccomandazioni di progettazione specifiche in base ai vantaggi e alle problemi descritti per l'input degli sguardi:

1. **Il controllo degli sguardi non è uguale a quello della testa:**
    - **Considerare se i movimenti degli occhi veloci ma incompleti si adattano all'attività di input:** Sebbene i nostri spostamenti rapidi e incompleti siano ottimi per selezionare rapidamente le destinazioni nel campo di visualizzazione, è meno applicabile per le attività che richiedono traiettorie di input uniformi, ad esempio la creazione o l'inclusione di annotazioni. In questo caso, è preferibile usare il puntamento con la mano o con la testa.
  
    - **Evitare di allungare direttamente gli sguardi degli utenti (ad esempio, un dispositivo di scorrimento o un cursore).**
Nel caso di un cursore, questo può comportare un effetto di "cursore in fuga" a causa di lievi offset nel segnale oculare proiettato. Nel caso di un dispositivo di scorrimento, può entrare in conflitto con il doppio ruolo del controllo del dispositivo di scorrimento con gli occhi, ma anche per verificare se l'oggetto si trova nella posizione corretta. Per l'esempio del dispositivo di scorrimento, è opportuno usare gli sguardi in combinazione con i movimenti della mano. Ciò significa che l'utente può passare rapidamente a un certo numero di dispositivi di scorrimento, sollevando la mano e pizzicando il pollice e l'indice per spostarlo. Quando il pizzico viene rilasciato, il dispositivo di scorrimento smette di essere spostato. In breve, gli utenti possono diventare sopraffatti e distratti, soprattutto se il segnale è impreciso per tale utente. 
  
2. **Combinare gli sguardi con gli altri input:** L'integrazione di Eye Tracking con altri input, ad esempio movimenti della mano, comandi vocali o pressioni dei pulsanti, offre diversi vantaggi:
    - **Consenti l'osservazione gratuita:** Dato che il ruolo principale degli occhi è osservare l'ambiente, è importante che gli utenti siano autorizzati a cercare senza attivare commenti o azioni (visivi, uditivi e così via). 
    La combinazione di rilevamento degli occhi con un altro controllo di input consente una transizione uniforme tra le modalità di osservazione e controllo di input.
  
    - **Potente provider di contesto:** L'uso di informazioni su dove e cosa si sta osservando quando si pronuncia un comando vocale o l'esecuzione di un gesto manuale consente di canalizzare senza interruzioni l'input nel campo della visualizzazione. Ad esempio, pronunciare _"put that there"_ per selezionare e posizionare in modo rapido e scorrevole un ologramma nella scena osservando semplicemente una destinazione e la destinazione desiderata. 

    - **Necessità di sincronizzare gli input multimodali:** Combinando rapidamente i movimenti degli occhi con input aggiuntivi più complessi, ad esempio i comandi di tipo Long Voice o i movimenti della mano, si rischia che l'utente continui a cercare prima che il comando di input aggiuntivo venga completato e riconosciuto. Di conseguenza, se si creano controlli di input personalizzati (ad esempio, movimenti della mano personalizzati), assicurarsi di registrare l'inizio di questo input o la durata approssimativa per correlarla a ciò che un utente ha esaminato in passato.
    
3. **Feedback sottile per l'input di rilevamento degli occhi:** È utile per fornire commenti e suggerimenti quando viene esaminata una destinazione per indicare che il sistema funziona come previsto, ma deve essere mantenuto sottile. Questo può includere la fusione lenta, l'interno e l'esterno, le evidenziazioni visive o eseguire altri comportamenti sottili della destinazione, ad esempio movimenti lenti, ad esempio un lieve aumento delle dimensioni di destinazione, per indicare che il sistema ha rilevato correttamente che l'utente sta esaminando una destinazione senza interrompere inutilmente il flusso di lavoro corrente dell'utente. 

4. **Evitare di applicare movimenti degli occhi non naturali come input:** Non forzare gli utenti a eseguire movimenti oculari specifici (movimenti sguardi) per attivare azioni nell'applicazione.

5. **Account per l'imprecisione:** Vengono distinti due tipi di imprecisioni che sono evidenti per gli utenti: offset e jitter. Il modo più semplice per risolvere un offset consiste nel fornire destinazioni sufficientemente grandi per interagire con. Si consiglia di usare un angolo visivo maggiore di 2 ° come riferimento. Ad esempio, l'anteprima è di circa 2 ° nell'angolo visivo quando si allunga il ARM. Segui pertanto le indicazioni seguenti:
    - Non forzare gli utenti a selezionare destinazioni minuscole. La ricerca ha dimostrato che se le destinazioni sono sufficientemente grandi e che il sistema è progettato correttamente, gli utenti ne descrivono le interazioni come semplice e magico. Se le destinazioni diventano troppo piccole, gli utenti descrivono l'esperienza come stancante e frustrante.
  
<br>

Questa pagina offre una panoramica corretta per iniziare a comprendere gli sguardi come input in realtà mista. Per iniziare a sviluppare, vedere le nostre informazioni sugli sguardi [in Unity](https://aka.ms/mrtk-eyes) e sugli [sguardi in DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Vedere anche
* [Comodità](comfort.md)
* [Eye-sguardi in DirectX](gaze-in-directx.md)
* [Eye-sguardi in Unity (Toolkit realtà mista)](https://aka.ms/mrtk-eyes)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Input vocale](voice-design.md)
