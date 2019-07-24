---
title: Modulo di apprendimento di base sulla realtà mista - Input avanzato
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f9da038fe917e9e45b386de54049d6aa312ecfba
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387782"
---
# <a name="6exploring-advanced-input-options"></a>6. esplorazione delle opzioni di input avanzate

In questa esercitazione vengono esaminate diverse opzioni di input avanzate per HoloLens 2, tra cui l'uso di comandi vocali, movimenti di panoramica e rilevamento degli occhi. 

## <a name="objectives"></a>Obiettivi

- Attivare eventi usando comandi vocali e parole chiave
- Usare le mani tracciate per la panoramica delle trame e degli oggetti 3D con le mani rilevate
- Sfruttare le funzionalità di rilevamento degli occhi di HoloLens 2 per selezionare gli oggetti

## <a name="instructions"></a>Istruzioni

### <a name="enabling-voice-commands"></a>Abilitazione dei comandi vocali

In questa sezione si implementeranno due comandi vocali. In primo luogo, verrà introdotta la possibilità di abilitare o disabilitare il pannello di diagnostica della frequenza dei fotogrammi indicando la funzionalità di attivazione/disimpostazione della diagnostica In secondo luogo, si esaminerà la possibilità di riprodurre un suono con un comando Voice. Per iniziare, verranno esaminati i profili e le impostazioni di MRTK responsabili della configurazione dei comandi vocali. 

1. Nella gerarchia della scena di base selezionare MixedRealityToolkit. Nel pannello Inspector scorrere verso il basso fino a impostazioni di sistema di input. Fai doppio clic per aprire il profilo del sistema di input. Clonare il profilo di sistema di input per renderlo modificabile come appreso nella [lezione 1](mrlearning-base-ch1.md) 

Nel profilo del sistema di input sono disponibili diverse impostazioni. Per i comandi vocali selezionare impostazioni dei comandi vocali. 

![Immagine lezione 5 capitolo 1 passaggio 2](images/Lesson5_Chapter1_step2im.PNG)

2. Clonare il profilo dei comandi vocali per renderlo modificabile come illustrato nella [lezione 1](mrlearning-base-ch1.md). Fare doppio clic sul profilo del comando vocale in cui si noterà un intervallo di impostazioni. Per una descrizione completa di queste impostazioni, fare riferimento alla [documentazione di MRTK Speech](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: come comportamento generale predefinito è impostato l'avvio automatico. Se lo si desidera, è possibile modificare l'avvio manuale. In questo esempio, tuttavia, l'avvio automatico verrà mantenuto. MRTK viene fornito con diversi comandi vocali predefiniti, ad esempio menu, Imposta/Rimuovi diagnostica e imposta/Nascondi Profiler. Si userà la parola chiave "attiva/disattiva diagnostica" per attivare e disattivare il contatore framerate di diagnostica. Aggiungeremo inoltre un nuovo comando vocale nei passaggi seguenti.
>
> ![Immagine nota lezione 5 capitolo 1](images/Lesson5_chapter1_noteim.PNG)

3. Aggiungi un nuovo comando vocale. Per aggiungere un nuovo comando Voice, fare clic sul pulsante + Aggiungi un nuovo riconoscimento vocale. Verrà visualizzata una nuova riga sotto l'elenco dei comandi vocali esistenti. Digita il comando vocale che vuoi usare. In questo esempio verrà usato il comando "Play Music".

>Suggerimento: poi anche impostare un valore di keycode per i comandi vocali. In questo modo, i comandi vocali possono attivare eventi quando si preme un tasto della tastiera.    

4. Aggiungi la capacità di rispondere ai comandi vocali. Selezionare un oggetto nella gerarchia della scena di base a cui non è associato alcun altro script di input (ad esempio, nessun gestore di manipolazione). Nel pannello Inspector fare clic su Add Component. Digitare "gestore di input vocale" per selezionarlo.

   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Per impostazione predefinita, vengono visualizzate due caselle di controllo. Uno è la casella di controllo è stato attivo obbligatorio. Ciò significa che si sta puntando a un oggetto con un raggio di sguardi, sguardi, sguardi, puntini di controllo o sguardi a mano, il comando Voice verrà attivato da. Deselezionare questa casella di controllo in modo che l'utente non debba esaminare l'oggetto per utilizzare il comando Voice.

5. Aggiungi la capacità di rispondere a un comando vocale. A tale scopo, fare clic sul pulsante + che si trova nel gestore di input vocale e selezionare la parola chiave a cui si desidera rispondere.

   > Nota: queste parole chiave vengono popolate in base al profilo che hai modificato nel passaggio precedente.

![Immagine lezione 5 capitolo 1 passaggio 5](images/Lesson5_chapter1_step5im.PNG)

6. Accanto a parola chiave verrà visualizzato un menu a discesa. Selezionare Attiva/Rimuovi diagnostica in modo che ogni volta che l'utente dice la frase "attiva/Rimuovi diagnostica", attiva un'azione. Si noti che potrebbe essere necessario espandere l'elemento 0 premendo la freccia accanto.

![Immagine lezione 5 capitolo 1 passaggio 6](images/Lesson5_chapter1_step6im.PNG)

7. Aggiungere lo script di controllo demo di diagnostica per attivare e disattivare la diagnostica del contatore di fotogrammi. A tale scopo, fare clic su Aggiungi componente e cercare script dei controlli demo di diagnostica e aggiungerlo dal menu. Questo script può essere aggiunto a qualsiasi oggetto. Per semplicità, tuttavia, verrà aggiunto allo stesso oggetto del gestore di input vocale. 

   > Nota: Questo script è incluso solo con questi moduli e non è incluso nel MRTK originale.

![Immagine lezione 5 capitolo 1 passaggio 7](images/Lesson5_chapter1_step7im.PNG)

8. Aggiungere una nuova risposta nel gestore di input vocale. A tale scopo, fare clic sul pulsante + sotto dove è indicato Response () (contrassegnato da freccia verde nell'immagine precedente).

![Immagine lezione 5 capitolo 1 passaggio 7](images/Lesson5_chapter1_step8.PNG)

9. Trascinare l'oggetto con lo script Diagnostics demo Controls per la nuova risposta appena creata nel passaggio 8.
    ![Immagine lezione 5 capitolo 1 passaggio 9](images/Lesson5_chapter1_step9im.PNG)

10. A questo punto, selezionare l'elenco a discesa "nessuna funzione" e selezionare controllo demo di diagnostica. Selezionare quindi la funzione attiva/disattiva diagnostica () che attiva e disattiva la diagnostica.  ![Immagine lezione 5 capitolo 1 passaggio 10](images/Lesson5_chapter1_step10im.PNG)
    
> Tieni presente che prima di creare il dispositivo devi abilitare le impostazioni del microfono. A tale scopo, fare clic su file e passare a impostazioni di compilazione, impostazioni lettore e verificare che sia impostata la funzionalità del microfono.

Si aggiungerà quindi la possibilità di riprodurre un file audio dal comando Voice usando l'oggetto Octa. Ricordare dalla [lezione 4](mrlearning-base-ch4.md) che è stata aggiunta la possibilità di riprodurre un clip audio da toccare l'oggetto Octa. Sfrutteremo la stessa origine audio per il comando vocale musicale.

11. Selezionare l'oggetto Octa nella gerarchia della scena di base.

12. Aggiungere un altro gestore di input vocale (ripetere i passaggi 4 e 5), ma con l'oggetto Octa. 

13. Anziché aggiungere il comando Imposta/Rimuovi voce di diagnostica del passaggio 6, aggiungere il comando Play Music Voice come illustrato nell'immagine seguente.
    
     ![Immagine lezione 5 capitolo 1 passaggio 13](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Come per i passaggi 8 e 9, aggiungere una nuova risposta e trascinare l'oggetto Octa nello slot di risposta vuoto.

15. Selezionare il menu a discesa che indica nessuna funzione. Quindi selezionare origine audio e selezionare PlayOneShot (AudioClip).

![Immagine lezione 5 capitolo 1 passaggio 15](images/Lesson5_chapter1_step15im.PNG)

16. Per questo esempio verrà usato lo stesso clip audio della [lezione 4](mrlearning-base-ch4.md). Passare al pannello del progetto, cercare il clip audio "MRTK_Gem" e trascinarlo nello slot di origine audio, come illustrato nell'immagine seguente. A questo punto l'applicazione risponderà ai comandi vocali "Imposta/Rimuovi diagnostica" per impostare il pannello del contatore frequenza dei fotogrammi e riprodurre musica per riprodurre la canzone MRTK_Gem.
     ![Immagine lezione 5 capitolo 1 passaggio 16](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Il movimento di panoramica 

In questa sezione verrà illustrato come utilizzare il gesto di panoramica. Questa operazione è utile per lo scorrimento usando il dito o la mano per scorrere il contenuto. È anche possibile usare il movimento Pan per ruotare gli oggetti, per scorrere una raccolta di oggetti 3D o anche per scorrere un'interfaccia utente 2D. Si apprenderà anche come usare il gesto di panoramica per decurvare una trama e come spostare una raccolta di oggetti 3D.

1. Crea un quadrilatero. Nella gerarchia di base della scena, fare clic con il pulsante destro del mouse, selezionare "oggetto 3D" e selezionare quad.

![Immagine lezione 5 capitolo 2 passaggio 2](images/Lesson5_chapter2_step2im.PNG)

2. Riposiziona il quadrilatero nel modo appropriato. Per questo esempio, si imposta x = 0, y = 0 e z = 1,5 fuori dalla fotocamera per una posizione comoda da HoloLens 2.

   > Nota: Se il quad si blocca o si trova davanti a qualsiasi contenuto delle lezioni precedenti, assicurarsi di spostarlo in modo che non blocchi gli altri oggetti.

3. Applica un materiale al quadrilatero. Questo sarà il materiale che scorreremo con il movimento di panoramica. 

![Immagine lezione 5 capitolo 2 passaggio 3](images/Lesson5_chapter2_step3im.PNG)

4. Nel pannello Progetti, digitare nella casella di ricerca "contenuto Pan". Trascina il materiale sul quadrilatero nella scena. 

> Nota: Il materiale di contenuto di Pan non è incluso in MRTK, ma è un asset nel pacchetto di asset del modulo come importato nelle lezioni precedenti. 

> Nota: quando aggiungi il contenuto per la panoramica, potrebbe avere un aspetto allungato. Puoi risolvere il problema modificando i valori x, y e z delle dimensioni del quadrilatero fino a ottenere l'aspetto desiderato.

Per usare il movimento di panoramica, avrai bisogno di un collisore sull'oggetto. Noterai che nel quadrilatero è già presente un collisore di tipo mesh. Tuttavia, questo tipo di collisore non è ideale, perché è estremamente sottile e difficile da selezionare. Consigliamo quindi di sostituirlo con un collisore cubico.

5. Fare clic con il pulsante destro del mouse su mesh Collider sul quad dal pannello Inspector. Quindi rimuoverlo facendo clic su Rimuovi componente.
    ![Immagine lezione 5 capitolo 2 passaggio 5](images/Lesson5_chapter2_step5im.PNG)
6. A questo punto, aggiungere la casella Collider facendo clic su Add Component (Aggiungi componente) e cercare "box Collider". la casella aggiuntiva di box Collider predefinita è troppo sottile, quindi fare clic sul pulsante modifica Collider per modificare. Quando il pulsante è premuto, puoi regolare le dimensioni usando i valori x, y e z o gli elementi nell'editor della scena. Per questo esempio, vogliamo estendere leggermente il collisore cubico dietro il quadrilatero. Nell'editor della scena trascina il collisore cubico dal retro verso l'esterno, come illustrato nell'immagine seguente. In questo modo, l'utente non solo USA il dito, ma l'intera mano per scorrere. 
    ![Immagine lezione 5 capitolo 2 passaggio 6](images/Lesson5_chapter2_step6im.PNG)
7. Configura l'interattività. Poiché si vuole interagire direttamente con il quad, si vuole usare il componente ritoccabile near Interaction che è stato usato nella lezione 4 per la riproduzione di musica dall'oggetto Octa. Fare clic su Aggiungi componente e cercare "near Interaction touchable" e selezionarlo come illustrato nelle immagini riportate di seguito. 

8. Aggiungi la capacità di riconoscere il movimento di panoramica. Fare clic su Add Component (Aggiungi componente) e digitare "Hand Interaction Pan". si avrà una scelta tra hand Ray (che consente di eseguire il panning da una distanza) e il dito dell'indice. Per questo esempio, manterremo impostata la seconda opzione. 
    ![Immagine lezione 5 capitolo 2 passaggio 7 immagine 8](images/Lesson5_chapter2_step7-8im.PNG)

![Immagine lezione 5 capitolo 2 passaggio 8](images/Lesson5_chapter2_step8im.PNG)

9. Nello script di Pan interazione con la mano, le caselle di controllo blocco orizzontale e blocco verticale bloccano i movimenti, rispettivamente. Le impostazioni della trama a capo rendono la trama (mapping trama) che segue i movimenti di Pan dell'utente. Per questo esempio, si verificherà tale casella. È inoltre disponibile la velocità attivo, che, se deselezionata, il movimento della panoramica non funzionerà. Seleziona anche questa casella. A questo punto si avrà un quad abilitato per Pan.

   

   Imparerai ora a fare una panoramica degli oggetti 3D. 

10. Fare clic con il pulsante destro del mouse sull'oggetto Quad, scegliere oggetto 3D, quindi cubo. Ridimensiona il cubo in modo che assuma approssimativamente i valori x = 0.1, y = 0.1 e z = 0.1. Copiare il cubo tre volte facendo clic con il pulsante destro del mouse sul cubo e premendo duplicato oppure premendo CTRL/comando D. distanziarli uniformemente. La scena dovrebbe avere un aspetto simile all'immagine seguente.

![Immagine lezione 5 capitolo 2 passaggio 10](images/Lesson5_chapter2_step10im.PNG)







11. Selezionare di nuovo il quad e, sotto lo script Hand Interaction Pan, impostare le azioni Pan su ognuno dei cubi. In ricevitori di eventi di Pan è necessario specificare il numero di oggetti che ricevono l'evento. Poiché sono presenti quattro cubi, digitare "4" e premere INVIO. Verranno visualizzati quattro campi vuoti.


![Immagine lezione 5 capitolo 2 passaggio 11](images/Lesson5_chapter2_step11im.PNG)



12. Trascinare ognuno dei cubi in ognuno degli slot degli elementi vuoti.
     ![Immagine lezione 5 capitolo 2 passaggio 12](images/Lesson5_chapter2_step12im.PNG)
    
13. Aggiungere lo script di spostamento con Pan a tutti i cubi premendo e tenendo premuto CTRL/Command e selezionando ogni oggetto. Dal pannello di controllo fare clic su Aggiungi componente e cercare "sposta con Pan". Fare clic sullo script per aggiungerlo a ogni cubo. Ora gli oggetti 3D verranno spostati con il movimento della panoramica. Se rimuovi il renderer della mesh sul quadrilatero, dovresti ottenere un quadrilatero invisibile in cui puoi fare una panoramica attraverso un elenco di oggetti 3D.

### <a name="eye-tracking"></a>Tracciamento oculare

In questa sezione verrà illustrato come abilitare la registrazione degli occhi nella demo. Le voci di menu 3D verranno spinte lentamente quando vengono osservate con lo sguardo. Attiveremo inoltre un effetto divertente al momento della selezione dell'oggetto fissato.

1. Verificare che i profili MRTK siano configurati correttamente. Al momento della stesura di questo documento, la configurazione dei profili di Mixed Reality Toolkit non include le funzionalità di tracciamento oculare per impostazione predefinita. Per aggiungere le funzionalità di rilevamento degli occhi, seguire le istruzioni riportate nella sezione "impostazione dei profili MRTK necessari per il rilevamento degli occhi", come descritto nella documentazione del Toolkit per la [realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Assicurarsi che la verifica degli occhi sia configurata correttamente attenendosi ai passaggi rimanenti nel collegamento alla documentazione precedente, ad esempio abilitando la verifica degli occhi in GazeProvider (il componente collegato alla fotocamera) e abilitando la simulazione del rilevamento degli occhi nell'editor di Unity. Si noti che le versioni future di MRTK possono includere la verifica degli occhi per impostazione predefinita.

    Il collegamento precedente consente di accedere a brevi istruzioni per:

    - Creazione dell'occhio provider di dati per l'uso nel profilo MRTK
    - Abilitare il tracciamento oculare nel provider di dati per lo sguardo fisso
    - Configurazione di una simulazione di rilevamento degli occhi nell'editor
    - Modificare le funzionalità della soluzione Visual Studio per consentire il tracciamento oculare nell'applicazione compilata

2. Aggiungi il componente Eye Tracking Target (Destinazione tracciamento oculare) agli oggetti di destinazione. Per consentire a un oggetto di rispondere agli eventi di sguardi occhi, è necessario aggiungere il componente EyeTrackingTarget in ogni oggetto con cui si vuole interagire usando lo sguardo a occhio. Aggiungi questo componente a ciascuno dei nove oggetti 3D che fanno parte della raccolta griglia. Suggerimento: Selezionare più elementi nella gerarchia per aggiungere in blocco il componente EyeTrackingTarget.
    ![Lezione 5 capitolo 3 passaggio 2](images/Lesson5Chapter3Step2.JPG)

3. A questo punto aggiungeremo lo script EyeTrackingTutorialDemo per alcune interessanti interazioni. Lo script EyeTrackingTutorialDemo è incluso nell'archivio della serie di esercitazioni. Non è incluso per impostazione predefinita con il Toolkit di realtà mista. Per ogni oggetto 3D nella raccolta della griglia, aggiungere lo script EyeTrackingTutorialDemo cercando il componente nel menu Aggiungi componente.
   ![Lezione 5 capitolo 3 passaggio 3](images/Lesson5Chapter3Step3.JPG)

4. Configura l'oggetto in modo da ruotare mentre il tuo sguardo è rivolto verso la destinazione. Si vuole configurare l'oggetto 3D per la rotazione mentre viene esaminato. A tale scopo, inserire un nuovo campo nell'oggetto durante la ricerca nella sezione target () del componente EyeTrackingTarget, come illustrato nell'immagine seguente. 

![Lezione 5 capitolo 3 passaggio 4a](images/Lesson5Chapter3Step4a.JPG)
![Lezione 5 capitolo 3 passaggio 4b](images/Lesson5Chapter3Step4b.JPG)



Nel campo appena creato aggiungere l'oggetto gioco corrente al campo vuoto e selezionare EyeTrackingTutorialDemo > RotateTarget () come illustrato nell'immagine seguente. L'oggetto 3D è ora configurato in modo da ruotare quando viene fissato con il tracciamento oculare. 

5. Aggiungere la possibilità di "blip target" (destinazione blip) a cui si sta osservando quando si fa clic su Select by Air-Tap o "Select". Analogamente al passaggio 4, si vuole attivare EyeTrackingTutorialDemo > BlipTarget () assegnandogli il campo Select () dell'oggetto Game del componente EyeTrackingTarget, come illustrato nella figura seguente. Con questa configurazione, si noterà un lieve blip nell'oggetto Game ogni volta che si attiva un'azione SELECT, ad esempio il tocco aereo o il comando Voice "Select". 
    ![Lezione 5 capitolo 3 passaggio 5](images/Lesson5Chapter3Step5.JPG)
6. Verifica che le funzionalità di tracciamento oculare siano configurate correttamente prima di compilarle in HoloLens 2. Al momento della stesura di questo articolo, Unity non è ancora in grado di impostare l'input dello sguardo per le funzionalità di rilevamento degli occhi. L'impostazione di questa funzionalità è necessaria per il funzionamento della verifica degli occhi in HoloLens 2. Per abilitare la funzionalità di input dello sguardo fisso, segui queste istruzioni nella documentazione di Mixed Reality Toolkit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>La procedura è stata completata. 
Sono state aggiunte le funzionalità di base per la registrazione degli occhi all'applicazione. Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare. Questo capitolo conclude inoltre la lezione 5, in cui sono state illustrate le funzionalità di input avanzate, ad esempio i comandi vocali, i movimenti di panoramica e il rilevamento degli occhi. 

[Lezione successiva: Esperienza di esempio di assemblaggio di un modulo lunare](mrlearning-base-ch6.md)

