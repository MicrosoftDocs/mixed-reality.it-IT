---
title: Case study - utilizzando spaziale audio in RoboRaid
description: Suono spaziale è una delle funzionalità più interessanti di Microsoft HoloLens, offrendo un modo per gli utenti potenzialmente percepita da cosa sta succedendo attorno a esse quando gli oggetti sono dalla linea di visuale.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, RoboRaid, spaziale audio
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600782"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Case study - utilizzando spaziale audio in RoboRaid

Charles Sinex, audio lead del team di esperienza Microsoft HoloLens, parla ha rilevato durante la creazione di audio per problematiche [RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j), un tiro a segno prima persona realtà mista.

## <a name="the-tech"></a>Le tecnologie innovative

[Suono spaziale](spatial-sound.md) è una delle funzionalità più interessanti di Microsoft HoloLens, offrendo un modo per gli utenti potenzialmente percepita da cosa sta succedendo attorno a esse quando gli oggetti sono dalla linea di visuale.

In RoboRaid, l'uso di più ovvia ed efficace del suono spaziale è avviso al lettore di qualcosa che accade all'esterno di visione artificiale periferici dell'utente. Ad esempio, il Breacher possibile immettere da una qualsiasi delle pareti analizzate nella chat room, ma se non si è rivolta verso la posizione in cui viene inserito, si potrebbero perdere. Per ricevere un avviso per questo invasion, ti faremo avere qualche distinti dell'audio proveniente da in cui viene immesso il Breacher, che consente di sapere che è necessario agire rapidamente per arrestarla.

## <a name="behind-the-scenes"></a>Dietro le quinte

Il processo di creazione suono spaziale per le app di HoloLens è così nuovi ed esclusivi e molti head imbattuto quando si verifica un problema può causare la mancanza di progetti precedenti da usare come riferimento. Si spera, questi esempi di sfide audio abbiamo affrontato mentre rendendo RoboRaid consentirà quando si creano audio per le proprie app.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenere conto del sovraccarico della CPU

Suono spaziale può essere impegnativa sulla CPU. Per un'esperienza di occupato, ad esempio RoboRaid è stato fondamentale mantenere le istanze di spaziali del suono con otto in qualsiasi momento. Nella maggior parte, è facile come impostazione del limite di istanze di diversi eventi audio in modo che tutte le istanze che si verificano dopo il raggiungimento del limite vengono terminate. Ad esempio, quando possibile distribuire i droni, loro screams sono limitati ai tre istanze in qualsiasi momento. Poiché si tratta solo di circa quattro dei droni è possono distribuire in una sola volta, tre screams disponibili una vasta gamma poiché non esiste alcun modo cervello può tenere traccia di che molti eventi audio con suono simile. Si liberano risorse per gli altri eventi audio spaziali, ad esempio esplosioni avversario o nemici preparazione di ripresa.

### <a name="rewarding-a-successful-dodge"></a>Gratificante scherma un esito positivo

Il meccanico dodging è uno degli aspetti più importanti dell'esperienza di gioco in RoboRaid e qualcosa che abbiamo ritenuto fosse davvero unico per l'esperienza di HoloLens. Di conseguenza, abbiamo deciso di rendere schiarisce riuscite molto gratificante al lettore. Abbiamo il Doppler "whizz-by" per sembrare interessanti piuttosto tempestivamente nello sviluppo. Inizialmente, l'idea era di utilizzare un ciclo e di modificarla in tempo reale usando volumi, il passo e filtro. L'implementazione per questa avrebbe dovuto essere molto elaborata, prima di eseguire il commit delle risorse per compilare effettivamente ciò abbiamo creato un prototipo ed economico usando un asset con l'effetto di Doppler incorporate per scoprire come viene feltro *. I dev talento fatta in modo che questo asset whizz da sarebbe riprodurre esattamente 0,7 secondi prima che il proiettile sarà stato superato da ear del lettore e i risultati ritenevano davvero incredibili! Inutile a dirsi, Microsoft ha rinunciato alla soluzione più complessa e implementato il prototipo.

* * (Se desiderate ulteriori informazioni sulla creazione di un asset audio con l'effetto di Doppler incorporato, consultare un articolo da Progettazione audio chiamato Charles Deenan [100 Whooshes in 2 minuti](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/).) *
<br>
![Correttamente schermare proiettile un nemico premia Windows Media player con un suono da whizz soddisfacente.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Abbandonando inefficace suoni

In origine, se avessimo volevamo Emetti segnale acustico protetti da Windows Media player un'esplosione dopo che aver schermato correttamente l'avversario proiettile, ma è stato deciso di scartare ciò per diversi motivi. In primo luogo, non è altrettanto efficace come è stato usato per lo scherma whizz-by SFX. Una volta che il proiettile raggiunge una parete sottostante è, qualcos'altro sarebbe successo del gioco che sarebbe piuttosto molto maschera con un suono. In secondo luogo, non abbiamo conflitto sul pavimento, in modo che è stato possibile ottenere l'esplosione di riprodurre quando il proiettile raggiunge il limite minimo anziché le pareti. E, infine, si è verificato l'utilizzo della CPU del suono spaziale. Il vostro nemico Elite Scorpion (uno che possono eseguire ricerche all'interno della parete) dispone di un attacco speciale che emette i proiettili circa otto. Non solo che è arrivata a seri problemi enorme nella combinazione, ha introdotto inoltre awful sono presenti perché è stato raggiunto della CPU troppo difficile.

### <a name="communicating-a-hit"></a>Un riscontro di comunicazione

Si è verificato, un problema interessante che abbiamo ritenuto fosse univoco per l'esperienza di HoloLens, è stata la difficoltà di comunicare in modo efficace per i lettori che sono stati raggiunti. Ciò che rende una realtà mista esperienza corretta è la sensazione che all'utente è in corso la storia. Ciò significa che si è incredibile pensare che si sta combattendo invasion un robot alieno nel tuo salotto.

I lettori ovviamente non è possibile alcuna operazione quando essi raggiunto, in modo che è stato necessario trovare un modo veramente convincere il giocatore che qualcosa cattivi avevano happed ad essi. Nei giochi convenzionale è possibile visualizzare un'animazione che consente di conoscere il carattere è eseguito un tentativo di accesso o la schermata potrebbe flash red team e i caratteri potrà grunt un po'. Poiché questi tipi di segnali non funzionano in un'esperienza di realtà mista, abbiamo deciso di combinare il segnale visivo con un suono davvero accentuato indicante che è stato impiegato danni. Creato un suono big data e rendeva così evidente nella combinazione di cui ducked tutti gli elementi verso il basso. Quindi, per evidenziarlo anche più, abbiamo aggiunto un breve segnale acustico di avvertimento come se il sink è stato un sub nucleare. 
<br>
![Quando viene raggiunto un lettore in RoboRaid, vedere un segnale visivo, ma anche ottenere una guida audio accentuata che li informa scattate danni.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Recupero di suono big data da relatori di piccole dimensioni

Relatori di HoloLens sono ridotti e chiaro soddisfare le esigenze del dispositivo, pertanto è impossibile prevedere lieti di ricevere troppo fascia bassa. Simile a scenari di sviluppo per Smartphone o dispositivi palmari giochi, audio finestre di progettazione e biografie sono necessario tenere in considerazione il contenuto di frequenza della loro audio. Sempre progettare suoni o scrivere musica con un intervallo di frequenza completo perché usura cuffie è un'opzione per gli utenti. Tuttavia, per garantire la compatibilità con i relatori HoloLens, eseguire un test occasionalmente inserendo un EQ nel master di qualsiasi DAW correntemente sia in uso. L'impostazione EQ è costituito da un filtro passa-alto circa 600 a 700 Hz (non troppo profonda) e passa-basso filtrare in circa 10 K (molto impegnativa). Questo dovrebbe farti un'idea approssimativa del modo in cui i suoni possibile riprodurre nel dispositivo.

Se si intende usare bassi per fornire il senso di corda cambierà tra la musica, è probabile che la musica perde completamente il senso di primo livello quando si applica questa impostazione EQ. Per risolvere questo problema, ho aggiunto un ulteriore livello al bassi che è un'ottava superiore (con alcune armoniche avanzate) e mista in modo da ottenere il senso di back radice. In alcuni casi con una distorsione a amp backup l'armoniche fornirà contenuto sufficiente frequenza nell'intervallo più alto per rendere il cervello che c'è qualcosa in esso contenuti. Questo vale per SFX come impatto, esplosioni o suoni per istante speciali, ad esempio con privilegi avanzati degli controllo completo attacchi. È davvero non è possibile basarsi sui requisiti minimi per fornire un senso di impatto o il peso di Windows Media player. Come con musica, grazie a una distorsione per offrire un po' di esaminarli ha sicuramente.

### <a name="making-your-audio-cues-stand-out"></a>Rendere i segnali acustici mettere in evidenza

Naturalmente, ogni membro del team voleva bombastic musica, proiettori l e pazzesco esplosioni; ma anche desiderano essere in grado di ascoltare voiceover o eventuali altri segnali acustici gioco-critical.

A un gioco di console con la gamma completa di frequenza sono disponibili altre opzioni per suddividere le frequenze a seconda dell'importanza del suono. Per RoboRaid, tuttavia, stavo limitato il numero di intervalli di frequenze che potrei curva da suoni. Ad esempio, se si usa il filtro passa basso e la curva esclude troppi dati terzultimo superiore dello spettro, non è necessario nulla sul suono a sinistra perché non è presente molto fascia bassa.

Per rendere RoboRaid audio paragonabile possibile sul dispositivo, abbiamo dovuto ridurre l'intervallo dinamico dell'intera esperienza e massiccio agli creando una gerarchia non crittografata di importanza per tipi diversi di suoni. Imposto il ducking tra -2 per dB-6 a seconda dell'importanza. Personalmente non mi piace ducking evidente nei giochi, in modo che ho trascorso molto tempo per la dissolvenza in/fuori intervallo e la quantità di attenuazione volume di ottimizzazione. È impostato i bus separati per spaziale audio, file audio non spaziale, ARMENO e il bus dry senza riverbero per la musica, quindi creati diversi dai bus di molto alta priorità, irreversibile e non critici. Gli asset sono stati quindi impostati per passare alla loro i bus appropriati.

Mi auguro che ci professionisti audio avrà quante entusiasmo lavorando le proprie App, come ho fatto lavorare su RoboRaid e divertenti. Non è possibile attendere prima di vedere (e ascolta!) cosa talento congratulo nuovamente all'esterno di Microsoft genererà per HoloLens.

## <a name="do-it-yourself"></a>Eseguire tale operazione manualmente

Un espediente ho scoperto per rendere determinati eventi (ad esempio esplosioni) audio "grandi", ad esempio la compilazione di chat room, ovvero consisteva nel creare un asset di mono per l'audio spaziale e con un asset stereo 2D, per essere riprodotti in 3D. Eseguire alcune operazioni di ottimizzazione, poiché con troppe informazioni nel contenuto stereo riduca al minimo la direzionalità degli asset di mono. Tuttavia, ottenere il saldo corretto comporterà suoni enorme che otterranno i lettori che attiva mentalmente nella giusta direzione.

È possibile provare a farlo da soli usando gli asset audio seguenti:

**Scenario 1**
1. Scaricare [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) e impostare per la riproduzione tramite spaziale audio e assegnarlo a un evento.
2. Scaricare [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) e impostare per la riproduzione nel formato stereo 2D e assegnare all'evento stesso come illustrato in precedenza. Poiché questi asset vengono normalizzati in Unity, attenuano volume di entrambi gli asset in modo che non vengono ritagliati.
3. Riprodurre insieme entrambi suoni. Spostare la testa circa sentirsi come spaziali sembra.

**Scenario 2**
1. Scaricare [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) e impostare per la riproduzione tramite spaziale audio e assegnare a un evento.
2. Riprodurre questo asset dalla stessa quindi confrontarlo con l'evento dello Scenario 1.
3. Provare a saldo diversi file di mono e stereo.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Engineer audio @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Spaziale audio](spatial-sound.md)
* [RoboRaid per Microsoft HoloLens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
