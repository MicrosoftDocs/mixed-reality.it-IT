---
title: Modulo MR Learning Base - avanzate Input
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929572"
---
# <a name="mr-learning-base-module---advanced-input"></a>Modulo MR Learning Base - avanzate Input

In questa lezione, esamineremo varie opzioni avanzate di input per il 2 HoloLens, incluso l'uso di comandi vocali, panoramica movimento e sotto controllo di rilevamento. 

## <a name="objectives"></a>Obiettivi

- Informazioni su come attivare eventi utilizzando le parole chiave e i comandi vocali
- Usare le mani rilevate per fare una panoramica di trame e oggetti 3D
- Sfruttare l'occhio del 2 HoloLens funzionalità per selezionare gli oggetti di rilevamento

## <a name="instructions"></a>Istruzioni

### <a name="enabling-voice-commands"></a>Abilitare i comandi vocali

In questa sezione, è necessario implementare due comandi vocali. Innanzitutto, la possibilità di attivare o disattivare il pannello di diagnostica di frequenza fotogrammi specificando "Attiva/Disattiva diagnostica". Secondo, la possibilità di riprodurre un suono con un comando vocale. Verranno innanzitutto analizzati i profili di MRTK e impostazioni responsabile per la configurazione di comandi vocali. 

1. Nella gerarchia della scena di Base selezionare "MixedRealityToolkit." Nel Pannello di controllo, scorrere verso il basso le impostazioni di sistema di input. Fare doppio clic per aprire il profilo di sistema di input. Clonare il profilo di sistema di input per renderlo modificabile, come illustrato in precedenza [lezione 1](mrlearning-base-ch1.md) 

Nel profilo di sistema di input, si noterà un'ampia gamma di impostazioni. Per i comandi vocali, andare in cui è visualizzato, "Impostazioni di comando di riconoscimento vocale". 

![Lesson5 capitolo 1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Clonare il profilo di comandi vocali per renderlo modificabile, come illustrato in precedenza [lezione 1](mrlearning-base-ch1.md). Fare doppio clic sul profilo del comando vocale, in cui si noterà una gamma di impostazioni. Per una descrizione completa su queste impostazioni, vedere la [documentazione su riconoscimento vocale MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: Per impostazione predefinita, il comportamento generale è l'avvio automatico. Che può essere modificato in manuale-inizio se lo si desidera, ma per questo esempio si userà per mantenerla in avvio automatico. Il MRTK include diversi comandi vocali predefiniti (ad esempio menu, attiva/disattiva diagnostica e profiler attiva/disattiva). Verrà usata la parola chiave "Attiva/Disattiva diagnostica" per attivare e disattivare il contatore di frequenza dei fotogrammi di diagnostica. Verrà inoltre aggiunto un nuovo comando vocale nei passaggi seguenti.
>
> ![Lesson5 capitolo 1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Aggiungere un nuovo comando vocali. Per aggiungere un nuovo comando vocale, fare clic sul pulsante "+ Aggiungi un nuovo comando speech" e si noterà una nuova riga verso il basso visualizzato sotto l'elenco di comandi vocali esistenti. Digitare il comando della voce da usare. In questo esempio musicample si intende usare il comando "Riproduci musica".

>Suggerimento: È anche possibile impostare un codice per i comandi vocali. In questo modo per i comandi vocali per attivare su preme un tasto della tastiera.   

4. Aggiungere la possibilità di rispondere a comandi vocali. Selezionare un oggetto qualsiasi nella gerarchia di scena base che non dispone di qualsiasi altro script di input collegato a esso (ad esempio, nessun gestore manipulation.) Nel Pannello di controllo, fare clic su "Aggiungi componente". Digitare "gestore input vocale." Selezionarla.
   ![Lesson5 capitolo 1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Per impostazione predefinita, si visualizzeranno le caselle di 2 controllo, uno è la casella di controllo "non è richiesto lo stato attivo". Ciò significa, purché facciano riferimento all'oggetto con un raggio sguardo, (visiva, head sguardo, controller sguardo o mano sguardo) verrà attivato il comando vocali. Deselezionare questa casella di controllo per fare in modo che l'utente dispone esaminare l'oggetto da usare i comandi vocali.

5. Aggiungere la possibilità di rispondere a un comando vocali. A tale scopo, selezionare la parola chiave per rispondere a fare clic sul pulsante "+" è il gestore di input vocale.

   > Nota: Queste parole chiave vengono popolate in base al profilo che è stato modificato nel passaggio precedente.

![Lesson5 capitolo 1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Accanto a "Parola chiave" verrà visualizzato un menu a discesa. Selezionare "Attiva/Disattiva diagnostica". In questo modo, in modo che ogni volta che l'utente indicato la frase "Attiva/Disattiva diagnostica" attiverà un'azione. Si noti che potrebbe essere necessario espandere "elemento 0" premere la freccia accanto a esso.

![Lesson5 capitolo 1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Aggiungere lo "diagnostica controllo script della demo" per attivare la diagnostica di contatore frequenza dei fotogrammi e disattivare. A tale scopo, premere il pulsante "Aggiungi componente" e cercare "script di controllo di diagnostica demo", quindi aggiungerlo di nuovo dal menu di scelta. Questo script può essere aggiunto a qualsiasi oggetto, ma per semplicità, si aggiungerà lo allo stesso oggetto come il gestore di input vocale. 

   > Nota: questo script è solo incluso con questi moduli e non è incluso con la MRTK originale.

![Lesson5 capitolo 1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Aggiungere una nuova risposta nel gestore di Input vocale. Scegliere il pulsante "+" sotto in cui verrà visualizzato il numero di "risposta ()" (contrassegnati da una freccia verde nella figura precedente).

![Lesson5 capitolo 1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Trascinare l'oggetto con lo script di controlli di diagnostica Demo per la nuova risposta che appena creato nel passaggio 8.
    ![Lesson5 capitolo 1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. A questo punto selezionare l'elenco a discesa "Nessuna funzione", selezionare i controlli di diagnostica demo e quindi "su Attiva/Disattiva diagnostica ()". Questa funzione consente di attivare la diagnostica e off.  ![Lesson5 capitolo 1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Si noti che prima della compilazione per il dispositivo è necessario abilitare le impostazioni di mic. A scopo quindi fare clic sul file, passare a impostazioni, da qui, le impostazioni del giocatore, compilazione e verificare che la funzionalità di microfono è impostata.

Successivamente, verrà aggiunta la possibilità di riprodurre un file audio da comandi vocali utilizzando l'oggetto "ottaidrato". Si ricorderà da [lezione 4](mrlearning-base-ch4.md), è stata aggiunta la possibilità di riprodurre clip audio da toccare l'oggetto ottaidrato. Per i comandi vocali musica verrà sfruttato questa stessa origine audio.

11. Selezionare l'oggetto ottaidrato nella gerarchia della scena di base.

12. Aggiungere un altro gestore input vocale (ripetere i passaggi 4 e 5), ma con l'oggetto ottaidrato. 

13. Anziché aggiungere il comando vocale "Attiva/Disattiva diagnostica" del passaggio 6, aggiungere il comando vocale "Riproduci musica", come illustrato nell'immagine seguente.
    
     ![Lesson5 capitolo 1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Come con i passaggi 8 e 9, aggiungere una nuova risposta e trascinare l'ottaidrato lo slot vuoto nella risposta.

15. Selezionare il menu a discesa con la dicitura "Nessuna funzione," selezionare "origine Audio", quindi selezionare "PlayOneShot (AudioClip)."

![Lesson5 capitolo 1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Per il clip audio, in questo esempio si userà per usare la stessa clip audio da [lezione 4](mrlearning-base-ch4.md). Passare al pannello del progetto, cercare "MRTK_Gem" clip audio e trascinarlo nello slot di origine audio, come illustrato nell'immagine seguente. A questo punto l'applicazione dovrebbe essere in grado di rispondere ai comandi vocali "Attiva/Disattiva diagnostica" per attivare o disattivare il pannello di contatore frequenza fotogrammi e "Riproduci musica" per riprodurre il brano MRTK_Gem.
     ![Lesson5 capitolo 1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Il movimento di zoom 

In questo capitolo, si apprenderà come usare il movimento di zoom. È utile per lo scorrimento (uso del dito o manualmente per scorrere il contenuto). È anche possibile usare il movimento di zoom per ruotare gli oggetti, per scorrere una raccolta di oggetti 3D, o persino scorrere un 2D dell'interfaccia utente. Microsoft learning come usare il movimento di zoom per alterare una trama. Verrà anche illustrato come spostare una raccolta di oggetti 3D.

1. Creare un quadrato. Nella gerarchia scena base, fare clic destro, selezionare "3D Object", quindi "Quad."

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Riposizionare il quad come appropriato. Per questo esempio, impostiamo la x = 0, y = 0 e il valore z Version=1.5 dalla camera per una posizione comoda da 2 HoloLens.

   > Nota: Se i blocchi quad (è per infront di) tutti i contenuti dalle lezioni precedenti, assicurarsi di spostare in modo che non blocca gli altri oggetti.

3. Applicare un materiale al quad. Questo materiale sarà il materiale che è sarà lo scorrimento di con il movimento di zoom. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. Nel Pannello di progetti, digitare nella casella di ricerca "pan contenuto". Trascinare questo materiale a quad nella scena. 

> Nota: Il materiale "Far scorrere il contenuto" non è incluso nel MRTK, ma è una risorsa nel pacchetto di asset dal modulo, come importato nelle lezioni precedenti. 

> Nota: Quando si aggiunge il contenuto di zoom, potrebbero essere estesa. È possibile risolvere il problema modificando i valori x, y e z i valori delle dimensioni dei / quad fino a quando non si è soddisfatti con l'aspetto.

Per usare il movimento di zoom, è necessario un collider sull'oggetto. È possibile riscontrare che il quad esiste già un collider mesh. Tuttavia, il collider mesh non è ideale, perché è estremamente ridotte e difficili da selezionare. È consigliabile sostituire l'oggetto collider mesh con un collider casella.

5. Fare clic con il pulsante destro l'oggetto collider mesh che si trova nel quad (nel Pannello di controllo), quindi rimuoverlo facendo clic su "Rimuovi componente". 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Ora aggiungere l'oggetto collider finestra facendo clic su "Aggiungi componente" e la ricerca di "casella collider". Il valore predefinito aggiunto collider finestra è ancora troppo magri, quindi fare clic sul pulsante "Modifica collider" per la modifica. Quando viene premuto, è possibile regolare le dimensioni usando x, y e z valori o gli elementi nell'editor di scena. In questo esempio si vuole estendere un po' oggetto collider casella dietro il quad. Nell'editor di scena, trascinare l'oggetto collider casella dal retro, esterno (vedere la figura seguente). Cosa si farà è consentire all'utente di usare non solo il dito, ma le mani intera da scorrere. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Rendere interattivo. Poiché si vuole interagire direttamente con il quadruplo processore, è opportuno utilizzare il componente "quasi interazione touchable" (abbiamo utilizzato anche in questo nella lezione 4 per la riproduzione di musica dall'ottaidrato). Fare clic su "Aggiungi componente" e cercare "quasi interazione touchable" e selezionare, come illustrato nelle immagini seguenti. 

8. Aggiungere la capacità di riconoscere il movimento di zoom. Fare clic su "Aggiungi componente" e digitare "pan interazione a mano". Hai una scelta tra ray mano (consentendo di eseguire una panoramica a distanza) e con un dito indice. Per questo esempio, lasciare il dito indice. 
    ![Lesson5 Chapter2 8Im passaggio 7](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. Nello script pan interazione manuale, il "blocco orizzontale" e le caselle di controllo "blocco verticale" bloccherà i movimenti, rispettivamente. Le impostazioni di trama a capo automatico renderà la trama (mapping di trama) seguire i movimenti di zoom dell'utente. In questo esempio verrà seleziona questa casella. È anche disponibile "velocity active" che, se non è selezionata, il movimento di zoom non funziona. Anche questa casella di controllo. A questo punto si avrà un quad pan-abilitata.

   

   Successivamente, si imparerà a fare una panoramica degli oggetti 3D. 

10. Fare clic con il pulsante destro dell'oggetto quad, selezionare l'oggetto 3D, quindi fare clic su "cubo". Scalabilità del cubo in modo che sia all'incirca x = 0,1, y = compresa tra 0.1 e z = 0,1. Copiare tale cubo 3 volte (facendo clic con il pulsante destro del cubo e premendo duplicati o dal controllo premendo/comando D). Distanziarli in modo uniforme. La scena dovrebbe essere simile all'immagine seguente.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Selezionare di nuovo il quad, e con lo script pan interazione manuale, sarà necessario impostare le azioni pan a ciascuno dei cubi. In "ricevitori di eventi pan" vogliamo specificare il numero di oggetti che ricevono l'evento. Poiché sono presenti 4 cubi, tipo "4" e premere INVIO. 4 campi vuoti devono essere visualizzati.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Trascinare ognuno dei cubi in ognuno degli slot elemento vuoto.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Aggiungere lo script "spostamento con pan" per tutti i cubi. Per eseguire questa operazione, premere e tenere premuto/comando di controllo e selezionare ogni oggetto. Quindi, nel Pannello di controllo, fare clic su "Aggiungi componente" e cercare "lo spostamento con pan". Fare clic sullo script e verrà aggiunto a ogni cubo. Ora gli oggetti 3D verranno spostata insieme il movimento di zoom. Se si rimuove il rendering mesh di quad, si avranno ora un quad invisibile in cui è possibile fare una panoramica di un elenco di oggetti 3D.

### <a name="eye-tracking"></a>Sotto controllo di rilevamento

In questo capitolo verrà illustrato come abilitare il rilevamento di occhio nella nostra demo. La voci di menu 3D si ruoterà lentamente quando sono in corso gazed al momento con sguardo sotto controllo. È anche attiverà una divertente effetto quando viene selezionato l'elemento gazed a una.

1. Verificare che siano configurati correttamente i profili di Toolkit di realtà mista. Al momento della stesura di questo documento, la configurazione del profilo di realtà mista toolkit non include sotto controllo le funzionalità di gestione per impostazione predefinita. Per aggiungere le funzionalità di gestione sotto controllo, seguire le istruzioni nella sezione "Configurare i profili MRTK necessari a tenere sotto controllo", come descritto nel [documentazione di Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Assicurarsi che sotto controllo di rilevamento è configurato correttamente eseguendo tutti i passaggi rimanenti nel collegamento di documentazione precedente, inclusa l'abilitazione di rilevamento di occhi in GazeProvider (componente collegato a fotocamera) e l'abilitazione di simulazione d'occhio rilevamento nell'editor di Unity. Si noti che la versione futura del MRTK può includere rilevamento occhio per impostazione predefinita.

    Il collegamento sopra riportato vengono fornite istruzioni breve per:

    - Creazione di un occhio estasiati Data Provider per l'uso nel profilo MRTK
    - Abilitazione del rilevamento delle occhio nel Provider estasiati
    - Configurare per la simulazione occhio rilevamento nell'editor
    - Funzionalità della soluzione Visual Studio per tenere traccia sotto controllo nell'applicazione compilata di modifica

2. Aggiungere il componente di destinazione di rilevamento agli oggetti di destinazione. Per consentire a un oggetto di rispondere agli eventi sguardo rossi, è necessario aggiungere il componente EyeTrackingTarget su ogni oggetto che si desidera interagire tramite sguardo sotto controllo. Aggiungere questo componente per ognuno degli oggetti 3D nove che fanno parte della raccolta della griglia. Suggerimento: selezionare più elementi nella gerarchia per il componente EyeTrackingTarget-Aggiungi in blocco.
    ![Passaggio 2 Chapter3 Lesson5](images/Lesson5Chapter3Step2.JPG)

3. Ora si aggiungerà lo script EyeTrackingTutorialDemo per alcune interazioni interessanti. Lo script EyeTrackingTutorialDemo è incluso come parte del repository di questa serie di esercitazioni e non è incluso per impostazione predefinita con il Toolkit di realtà mista. Per ogni oggetto 3D nell'insieme della griglia, aggiungere lo script EyeTrackingTutorialDemo eseguendo una ricerca per il componente nel menu "Aggiungi componente".
   ![Passaggio 3 Chapter3 Lesson5](images/Lesson5Chapter3Step3.JPG)

   4. Ruotare l'oggetto durante la ricerca nella destinazione. Vorremmo configurare l'oggetto 3D da ruotare mentre si sta esaminando. A tale scopo, inserire un nuovo campo nella sezione "Durante la ricerca in Target" del componente EyeTrackingTarget, come illustrato nell'immagine seguente. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



Nel campo appena creato, aggiungere l'oggetto gioco corrente per il campo vuoto e selezionare EyeTrackingTutorialDemo > RotateTarget() come illustrato nell'immagine seguente. L'oggetto 3D è ora configurato per rotazione quando è in corso gazed al momento si utilizza il rilevamento sotto controllo. 

5. Aggiungere capacità a "destinazione di problema" che è in corso gazed al momento di selezionare (-indice puntato, o pronunciare "selezionare"). Analogamente al passaggio 4, che si vuole attivare EyeTrackingTutorialDemo > BlipTarget() assegnandolo al campo "Select ()" dell'oggetto gioco del componente EyeTrackingTarget, come illustrato nella figura seguente. Con questa configurazione a questo punto, si noterà un problema di lieve nell'oggetto di gioco ogni volta che si attiva un'azione Seleziona, ad esempio-indice puntato o i comandi vocali "seleziona". 
    ![Passaggio 5 Chapter3 Lesson5](images/Lesson5Chapter3Step5.JPG)
6. Verificare le funzionalità di gestione sotto controllo siano configurate correttamente prima della compilazione a HoloLens 2. Al momento della stesura di questo documento, Unity non ancora disponibile la possibilità di impostare la capacità di input (per il rilevamento rossi) sguardo. L'impostazione di questa funzionalità è necessaria per il rilevamento di occhio lavorare su 2 HoloLens. Seguire queste istruzioni nella documentazione di toolkit di realtà mista per abilitare la funzionalità di input sguardo: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>La procedura è stata completata. 
È stato aggiunto correttamente base sotto controllo le funzionalità di gestione all'applicazione. Queste azioni sono solo l'inizio di un mondo di possibilità con sotto controllo di rilevamento. In questo capitolo articolo conclude anche lezione 5, in cui sono state apprese funzionalità avanzate di input, ad esempio comandi vocali, la panoramica di movimenti e rilevamento sotto controllo. 

[Lezione successiva: Esperienza di esempio di modulo lunare Assembly](mrlearning-base-ch6.md)

