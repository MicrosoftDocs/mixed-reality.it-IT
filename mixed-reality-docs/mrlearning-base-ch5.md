---
title: Esercitazioni introduttive-6. Esplorazione delle opzioni di input avanzate
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926541"
---
# <a name="6-exploring-advanced-input-options"></a>6. esplorazione delle opzioni di input avanzate

In questa esercitazione vengono esplorate diverse opzioni di input avanzate per HoloLens 2, tra cui l'uso di comandi vocali, movimenti di panoramica e rilevamento degli occhi. 

## <a name="objectives"></a>Obiettivi

- Attivare eventi usando comandi vocali e parole chiave
- Usare le mani tracciate per la panoramica delle trame e degli oggetti 3D con le mani rilevate
- Sfruttare le funzionalità di rilevamento degli occhi di HoloLens 2 per selezionare gli oggetti

## <a name="instructions"></a>Istruzioni

### <a name="enabling-voice-commands"></a>Abilitazione dei comandi vocali

In questa sezione vengono implementati due comandi vocali. In primo luogo, la possibilità di abilitare o disabilitare il pannello diagnostica frequenza frame viene introdotta con la dicitura "Disabilita diagnostica". In secondo luogo, viene analizzata la possibilità di riprodurre un suono con un comando Voice. I profili e le impostazioni di MRTK responsabili della configurazione dei comandi vocali vengono esaminati per primi.

1. Nella gerarchia di BaseScene selezionare MixedRealityToolkit. Quindi, nel pannello Inspector selezionare input e fare clic sul pulsante Small clone a sinistra del DefaultMixedRealityInputSystemProfile per aprire il popup del profilo clone. Nella finestra popup fare clic su Clona per creare un nuovo profilo MixedRealityInputSystemProfile.

    ![mrlearning-base-CH5-1-step1a. png](images/mrlearning-base-ch5-1-step1a.png)

    Viene anche popolato automaticamente il MixedRealityToolkitConfigurationProfile con il MixedRealityInputSystemProfile appena creato.

    ![mrlearning-base-CH5-1-step1b. png](images/mrlearning-base-ch5-1-step1b.png)

2. Nel profilo del sistema di input sono disponibili diverse impostazioni. Per i comandi vocali, espandere la sezione Speech e seguire lo stesso processo del passaggio precedente per clonare il DefaultMixedRealitySpeechCommandsProfile e sostituirlo con la copia modificabile.

    ![mrlearning-base-CH5-1-Step2. png](images/mrlearning-base-ch5-1-step2.png)

    Nel profilo del comando vocale si noterà un intervallo di impostazioni. Per una descrizione completa di queste impostazioni, fare riferimento alla [documentazione di MRTK Speech](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).

    come comportamento generale predefinito è impostato l'avvio automatico. Questa operazione può essere modificata in manuale-avvio, se necessario. Tuttavia, per questo esempio, mantenerlo all'avvio automatico. MRTK viene fornito con diversi comandi vocali predefiniti, ad esempio menu, Visualizza/Nascondi diagnostica e imposta/Nascondi Profiler. Si userà la parola chiave "attiva/disattiva diagnostica" per attivare e disattivare il contatore framerate di diagnostica. Aggiungeremo inoltre un nuovo comando vocale nei passaggi seguenti.

3. Aggiungi un nuovo comando vocale. A tale scopo, fare clic sul pulsante + Aggiungi un nuovo riconoscimento vocale. Verrà visualizzata una nuova riga sotto l'elenco dei comandi vocali esistenti. Digitare il comando vocale che si vuole usare. In questo esempio, usare il comando "Play Music".

    ![mrlearning-base-CH5-1-step3. png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >poi anche impostare un valore di keycode per i comandi vocali. In questo modo, i comandi vocali possono attivare eventi quando si preme un tasto della tastiera.

4. Aggiungi la capacità di rispondere ai comandi vocali. Selezionare un oggetto nella gerarchia BaseScene a cui non sono associati altri script di input, ad esempio l'oggetto gioco MixedRealityPlayspace. Nel pannello Inspector fare clic su Add Component, cercare "speech" e selezionare lo script del gestore di input vocale.

    ![mrlearning-base-CH5-1-step4. png](images/mrlearning-base-ch5-1-step4.png)

    Per impostazione predefinita, vengono visualizzate due caselle di controllo. Uno è la casella di controllo è stato attivo obbligatorio. Quindi, fino a quando si punta all'oggetto con un raggio di sguardi, un occhio, un controller o uno sguardo a mano, il comando Voice verrà attivato. Deselezionare questa casella di controllo in modo che l'utente non debba esaminare l'oggetto per utilizzare il comando Voice.

5. Aggiungi la capacità di rispondere a un comando vocale. A tale scopo, fare clic sul pulsante + che si trova nel gestore di input vocale.

    ![mrlearning-base-CH5-1-STEP5. png](images/mrlearning-base-ch5-1-step5.png)

6. Accanto a parola chiave verrà visualizzato un menu a discesa. Selezionare Attiva/Rimuovi diagnostica in modo che ogni volta che l'utente dice la frase "attiva/Rimuovi diagnostica", attiva un'azione. Si noti che potrebbe essere necessario espandere l'elemento 0 premendo la freccia accanto.

    ![mrlearning-base-CH5-1-step6. png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >Queste parole chiave vengono popolate in base al profilo modificato nel passaggio 3.

7. Aggiungere lo script dei controlli voce del sistema di diagnostica per attivare e disattivare la diagnostica del contatore di fotogrammi. A tale scopo, fare clic su Aggiungi componente, cercare lo script dei controlli voce del sistema di diagnostica e aggiungerlo dal menu. Questo script può essere aggiunto a qualsiasi oggetto, ma per semplicità lo aggiungeremo allo stesso oggetto del gestore di input vocale.

    ![mrlearning-base-CH5-1-STEP7. png](images/mrlearning-base-ch5-1-step7.png)

8. Aggiungere una nuova risposta nel gestore di input vocale. A tale scopo, fare clic sull'icona "+" per aggiungere una nuova risposta all'elenco risposta.

    ![mrlearning-base-CH5-1-Step8. png](images/mrlearning-base-ch5-1-step8.png)

9. Trascinare l'oggetto che contiene lo script dei controlli voce del sistema di diagnostica per la nuova risposta appena creata nel passaggio precedente.

    ![mrlearning-base-CH5-1-step9. png](images/mrlearning-base-ch5-1-step9.png)

10. Fare clic sull'elenco a discesa funzione (in cui non è presente alcuna funzione), quindi controllare i controlli voce del sistema di diagnostica e selezionare la funzione ToggleDiagnostics () che attiva e disattiva la diagnostica.

    ![mrlearning-base-CH5-1-Step10. png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > Prima di creare il dispositivo, è necessario abilitare le impostazioni MIC. A tale scopo, fare clic su file e passare a impostazioni di compilazione, impostazioni lettore e verificare che sia impostata la funzionalità Microphone.

    Aggiungere quindi la possibilità di riprodurre un file audio dal comando Voice usando l'oggetto Octa. Ricordare dalla [lezione 4](mrlearning-base-ch4.md) che è stata aggiunta la possibilità di riprodurre un clip audio da toccare l'oggetto Octa. Sfrutteremo la stessa origine audio per il comando vocale musicale.

11. Selezionare l'oggetto Octa nella gerarchia di BaseScene.

12. Aggiungere un altro gestore di input vocale (ripetere i passaggi 4 e 5), ma con l'oggetto Octa.

13. Anziché aggiungere il comando Imposta/Rimuovi voce di diagnostica del passaggio 6, aggiungere il comando Play Music Voice come illustrato nell'immagine seguente.

    ![mrlearning-base-CH5-1-step13. png](images/mrlearning-base-ch5-1-step13.png)

14. Come per i passaggi 8 e 9, aggiungere una nuova risposta e trascinare l'oggetto Octa, l'oggetto con lo script dei controlli voce del sistema di diagnostica, nello slot di risposta vuoto.

15. Selezionare il menu a discesa che indica nessuna funzione. Quindi selezionare origine audio, seguita da PlayOneShot (AudioClip).

    ![Immagine lezione 5 capitolo 1 passaggio 15](images/Lesson5_chapter1_step15im.PNG)

16. Per questo esempio verrà usato lo stesso clip audio della [lezione 4](mrlearning-base-ch4.md). Passare al pannello del progetto, cercare il clip audio "MRTK_Gem" e trascinarlo nello slot di origine audio, come illustrato nell'immagine seguente. A questo punto l'applicazione risponderà ai comandi vocali "Imposta/Rimuovi diagnostica" per impostare il pannello del contatore frequenza dei fotogrammi e riprodurre musica per riprodurre il MRTK_Gem brano.

    ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a>Il movimento di panoramica

In questa sezione verrà illustrato come utilizzare il gesto di panoramica. Questa operazione è utile per lo scorrimento usando il dito o la mano per scorrere il contenuto. È anche possibile usare il movimento Pan per ruotare gli oggetti, scorrere una raccolta di oggetti 3D o anche per scorrere un'interfaccia utente 2D. <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. Crea un quadrilatero. Nella gerarchia di BaseScene fare clic con il pulsante destro del mouse su e selezionare "oggetto 3D" seguito da quad.

    ![Immagine lezione 5 capitolo 2 passaggio 2](images/Lesson5_chapter2_step2im.PNG)

2. Riposizionare il quad, a seconda dei casi. Per questo esempio, si imposta x = 0, y = 0 e z = 1,5 fuori dalla fotocamera per una posizione comoda da HoloLens 2.

    >[!NOTE]
    >Se il quad si blocca o si trova davanti a qualsiasi contenuto delle lezioni precedenti, assicurarsi di spostarlo in modo che non blocchi gli altri oggetti.

3. Applica un materiale al quadrilatero. Questo materiale sarà quello che verrà eseguito scorrendo con il gesto di panoramica.

    ![Immagine lezione 5 capitolo 2 passaggio 3](images/Lesson5_chapter2_step3im.PNG)

4. Nel pannello Progetti, digitare "panning contenuto" nella casella di ricerca. Trascinare il materiale sul quad nella scena.

    >[!NOTE]
    >Il materiale di contenuto di Pan non è incluso in MRTK, ma è un asset nel pacchetto di asset del modulo come importato nelle lezioni precedenti.

    >[!NOTE]
    >quando aggiungi il contenuto per la panoramica, potrebbe avere un aspetto allungato. Puoi risolvere il problema modificando i valori x, y e z delle dimensioni del quadrilatero fino a ottenere l'aspetto desiderato.

    Per usare il movimento di panoramica, avrai bisogno di un collisore sull'oggetto. Noterai che nel quadrilatero è già presente un collisore di tipo mesh. Tuttavia, questo tipo di collisore non è ideale, perché è estremamente sottile e difficile da selezionare. Consigliamo quindi di sostituirlo con un collisore cubico.

5. Fare clic con il pulsante destro del mouse su mesh Collider sul quad dal pannello Inspector. Quindi rimuoverlo facendo clic su Rimuovi componente.

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. A questo punto, aggiungere la casella Collider facendo clic su Aggiungi componente e cercando "box Collider". Il conflitto di box aggiunto predefinito è ancora troppo sottile, quindi fare clic sul pulsante modifica Collider per modificarlo. Quando il pulsante è premuto, puoi regolare le dimensioni usando i valori x, y e z o gli elementi nell'editor della scena. Per questo esempio, vogliamo estendere leggermente il collisore cubico dietro il quadrilatero. Nell'editor della scena trascina il collisore cubico dal retro verso l'esterno, come illustrato nell'immagine seguente. In questo modo, l'utente non solo USA il dito, ma l'intera mano per scorrere.

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. Configura l'interattività. Poiché si vuole interagire direttamente con il quad, si vuole usare il componente ritoccabile near Interaction che è stato usato nella lezione 4 per la riproduzione di musica dall'oggetto Octa. Fare clic su Aggiungi componente, cercare "near Interaction touchable" e selezionarlo come illustrato nelle immagini riportate di seguito.

    ![mrlearning-base-CH5-2-step7a. png](images/mrlearning-base-ch5-2-step7a.png)

    Se viene visualizzato un avviso giallo relativo ai limiti e/o al centro non corrispondenti alle dimensioni e/o al centro del BoxCollider, fare clic sui pulsanti Correggi limiti e/o Correggi centro per aggiornare i valori del centro e dei limiti.

    ![mrlearning-base-CH5-2-step7b. png](images/mrlearning-base-ch5-2-step7b.png)

8. Aggiungi la capacità di riconoscere il movimento di panoramica. Fare clic su Aggiungi componente, digitare "interazione della mano" nel campo di ricerca e aggiungere il componente script zoom Hand Action Pan.

    ![mrlearning-base-CH5-2-step8a. png](images/mrlearning-base-ch5-2-step8a.png)

    E con questo, è disponibile un quad abilitato per Pan.

    Come si può notare, il componente Zoom Pan per l'interazione diretta ha diverse impostazioni, come esercizio facoltativo, che è possibile usare.

    ![mrlearning-base-CH5-2-step8b. png](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a>Tracciamento oculare

In questa sezione verrà illustrato come abilitare la registrazione degli occhi nella demo. Le voci di menu 3D verranno spinte lentamente quando vengono osservate con lo sguardo. Attiveremo inoltre un effetto divertente al momento della selezione dell'oggetto fissato.

1. Verificare che i profili MRTK siano configurati correttamente per la verifica degli occhi. Per eseguire questa operazione, vedere le istruzioni [Introduzione a Eye Tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) e verificare che la verifica degli occhi sia configurata correttamente esaminando la procedura descritta nella sezione [Setting up Eye Tracking](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) . Completare tutti i passaggi rimanenti della documentazione.

    >[!NOTE]
    >Se è stato usato DefaultHoloLens2InputSystemProfile, come illustrato nella lezione [configurare il Toolkit di realtà mista](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) , per clonare il profilo di configurazione MRTK personalizzato, il rilevamento degli occhi è abilitato per impostazione predefinita nel progetto Unity, ma è comunque necessario configurare la simulazione di rilevamento degli occhi per l'editor di Unity e configurare Visual Studio per consentire la verifica degli occhi per la compilazione.

    Il collegamento precedente consente di accedere a brevi istruzioni per:

    - Creazione di un provider di dati di sguardi reali misti di Windows per l'uso nel profilo MRTK
    - Abilitazione del rilevamento degli occhi nel provider di sguardi collegato alla fotocamera
    - Configurazione di una simulazione di rilevamento degli occhi nell'editor di Unity
    - Modificare le funzionalità della soluzione Visual Studio per consentire il tracciamento oculare nell'applicazione compilata

2. Aggiungi il componente Eye Tracking Target (Destinazione tracciamento oculare) agli oggetti di destinazione. Per consentire a un oggetto di rispondere agli eventi di sguardi occhi, è necessario aggiungere il componente EyeTrackingTarget in ogni oggetto con cui si vuole interagire usando lo sguardo a occhio. Aggiungi questo componente a ciascuno dei nove oggetti 3D che fanno parte della raccolta griglia.

    >[!TIP]
    >È possibile utilizzare i tasti MAIUSC e/o CTRL per selezionare più elementi nella gerarchia della scena e quindi aggiungere in blocco il componente EyeTrackingTarget.

    ![Chapter3 Lesson5 2](images/Lesson5Chapter3Step2.JPG)

3. Si aggiungerà quindi lo script EyeTrackingTutorialDemo per alcune interessanti interazioni. Lo script EyeTrackingTutorialDemo è incluso nell'archivio della serie di esercitazioni. Non è incluso per impostazione predefinita con il Toolkit di realtà mista. Per ogni oggetto 3D nella raccolta della griglia, aggiungere lo script EyeTrackingTutorialDemo cercando il componente nel menu Aggiungi componente.

   ![Lesson5 Chapter3 passaggio 3](images/Lesson5Chapter3Step3.JPG)

4. Configura l'oggetto in modo da ruotare mentre il tuo sguardo è rivolto verso la destinazione. Si vuole configurare gli oggetti 3D da ruotare mentre vengono esaminati. A tale scopo, inserire un nuovo campo nell'oggetto durante la ricerca nella sezione target () del componente EyeTrackingTarget, come illustrato nell'immagine seguente.

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    Nel campo appena creato aggiungere l'oggetto gioco corrente al campo vuoto e selezionare EyeTrackingTutorialDemo > RotateTarget (), come illustrato nell'immagine seguente. L'oggetto 3D è ora configurato in modo da ruotare quando viene fissato con il tracciamento oculare.

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. Aggiungere la possibilità di "blip target" (destinazione blip) a cui si sta osservando quando si fa clic su Select by Air-Tap o "Select". Analogamente al passaggio 4, si vuole attivare EyeTrackingTutorialDemo > BlipTarget () assegnandogli il campo Select () dell'oggetto Game del componente EyeTrackingTarget, come illustrato nella figura seguente. Con questa configurazione, si noterà un lieve blip nell'oggetto Game ogni volta che si attiva un'azione SELECT, ad esempio il tocco aereo o il comando Voice "Select".

    ![Lesson5 Chapter3 passaggio 5](images/Lesson5Chapter3Step5.JPG)

6. Verifica che le funzionalità di tracciamento oculare siano configurate correttamente prima di compilarle in HoloLens 2. Al momento della stesura di questo articolo, Unity non è ancora in grado di impostare l'input dello sguardo per le funzionalità di rilevamento degli occhi. L'impostazione di questa funzionalità è necessaria per il funzionamento della verifica degli occhi in HoloLens 2. Per abilitare la funzionalità di input di sguardi, seguire le istruzioni per [testare l'app Unity in un HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .

## <a name="congratulations"></a>Lezione completata

Sono state aggiunte le funzionalità di base per la registrazione degli occhi all'applicazione. Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare. Questo capitolo conclude inoltre la lezione 5, in cui sono state illustrate le funzionalità di input avanzate, ad esempio i comandi vocali, i movimenti di panoramica e il rilevamento degli occhi.

[Lezione successiva: 7. creazione di un'applicazione di esempio del modulo Lunar](mrlearning-base-ch6.md)
