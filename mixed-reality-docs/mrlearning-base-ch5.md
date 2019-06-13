---
title: Modulo di apprendimento di base sulla realtà mista - Input avanzato
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719892"
---
# <a name="mr-learning-base-module---advanced-input"></a>Modulo di apprendimento di base sulla realtà mista - Input avanzato

In questa lezione esamineremo varie opzioni di input avanzate per HoloLens 2, come l'uso di comandi vocali, il movimento di panoramica e il tracciamento oculare. 

## <a name="objectives"></a>Obiettivi

- Apprendere come attivare gli eventi usando parole chiave e comandi vocali
- Usare le mani tracciate per fare una panoramica di trame e oggetti 3D
- Sfruttare le funzionalità di tracciamento oculare di HoloLens 2 per selezionare gli oggetti

## <a name="instructions"></a>Istruzioni

### <a name="enabling-voice-commands"></a>Abilitazione dei comandi vocali

In questa sezione implementeremo due comandi vocali. Il primo consente di attivare o disattivare il pannello di diagnostica della frequenza dei fotogrammi pronunciando "toggle diagnostics". Il secondo consente di riprodurre un suono. Prima di tutto esamineremo i profili e le impostazioni di MRTK che sono responsabili della configurazione di comandi vocali. 

1. Nella gerarchia della scena di base seleziona "MixedRealityToolkit". Nel pannello di controllo scorri verso il basso fino alle impostazioni del sistema di input. Fai doppio clic per aprire il profilo del sistema di input. Clona il profilo del sistema di input per renderlo modificabile, come illustrato in precedenza nella [lezione 1](mrlearning-base-ch1.md) 

Nel profilo del sistema di input è presente un'ampia gamma di impostazioni. Per i comandi vocali, scorri verso il basso fino a "Speech Command Settings" (Impostazioni comandi vocali). 

![Immagine lezione 5 capitolo 1 passaggio 2](images/Lesson5_Chapter1_step2im.PNG)

2. Clona il profilo dei comandi vocali per renderlo modificabile, come illustrato in precedenza nella [lezione 1](mrlearning-base-ch1.md). Fai doppio clic sul profilo dei comandi vocali, in cui noterai un'ampia gamma di impostazioni. Per una descrizione completa su queste impostazioni, vedi la [documentazione sui comandi vocali di MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: come comportamento generale predefinito è impostato l'avvio automatico. Puoi modificare questo comportamento in avvio manuale, ma ai fini di questo esempio manterremo l'impostazione di avvio automatico. In MRTK sono inclusi diversi comandi vocali predefiniti, come Menu, Toggle Diagnostics (Attiva/Disattiva diagnostica) e Toggle Profiler (Attiva/Disattiva profiler). Useremo la parola chiave "toggle diagnostics" per abilitare e disabilitare il contatore della frequenza dei fotogrammi per la diagnostica. Aggiungeremo inoltre un nuovo comando vocale nei passaggi seguenti.
>
> ![Immagine nota lezione 5 capitolo 1](images/Lesson5_chapter1_noteim.PNG)

3. Aggiungi un nuovo comando vocale. Per aggiungere un nuovo comando vocale, fai clic sul pulsante "+ Add a New Speech Command" (Aggiungi un nuovo comando vocale). Noterai una nuova riga sotto l'elenco dei comandi vocali esistenti. Digita il comando vocale che vuoi usare. In questo esempio musicale useremo il comando "Play Music" (Riproduci musica).

>Suggerimento: poi anche impostare un valore di keycode per i comandi vocali. In questo modo, i comandi vocali vengono attivati in seguito alla pressione di un tasto sulla tastiera.   

4. Aggiungi la capacità di rispondere ai comandi vocali. Nella gerarchia della scena di base seleziona un oggetto a cui non siano associati altri script di input. Ad esempio, non selezionare un gestore di manipolazione. Nel pannello di controllo fai clic su "Add Component" (Aggiungi componente). Digita "speech input handler". Seleziona il componente.
   ![Immagine lezione 5 capitolo 1 passaggio 4](images/Lesson5_chapter1_step4im.PNG)

   

Per impostazione predefinita, verranno visualizzate due caselle di controllo, una delle quali è "Is Focus Required" (Stato attivo richiesto). Ciò significa che il comando vocale viene attivato solo quando l'utente punta all'oggetto tramite un raggio fisso (con lo sguardo, la testa, il controller o la mano). Deseleziona questa casella di controllo per fare in modo che l'utente non sia costretto a guardare l'oggetto per usare il comando vocale.

5. Aggiungi la capacità di rispondere a un comando vocale. Per eseguire questa operazione, fai clic sul pulsante "+" nel gestore di input vocale e seleziona la parola chiave a cui vuoi rispondere.

   > Nota: queste parole chiave vengono popolate in base al profilo che hai modificato nel passaggio precedente.

![Immagine lezione 5 capitolo 1 passaggio 5](images/Lesson5_chapter1_step5im.PNG)

6. Accanto a "Keyword" (Parola chiave) verrà visualizzato un menu a discesa. Seleziona "Toggle Diagnostics" (Attiva/Disattiva diagnostica). In questo modo, ogni volta che l'utente pronuncia "Toggle Diagnostics", viene attivata un'azione. Tieni presente che può essere necessario espandere "Element 0" (Elemento 0) selezionando la freccia visualizzata accanto.

![Immagine lezione 5 capitolo 1 passaggio 6](images/Lesson5_chapter1_step6im.PNG)

7. Aggiungi lo script "Diagnostics Demo Controls" (Controlli demo diagnostica) per attivare o disattivare il contatore della frequenza dei fotogrammi per la diagnostica. Per eseguire questa operazione, fai clic sul pulsante "Aggiungi componente" (Aggiungi componente), cerca lo script "diagnostics demo controls" e quindi aggiungilo dal menu. Questo script può essere aggiunto a qualsiasi oggetto, ma per semplicità lo aggiungeremo allo stesso oggetto del gestore di input vocale. 

   > Nota: questo script è incluso solo in questi moduli e non è disponibile nella versione originale di MRTK.

![Immagine lezione 5 capitolo 1 passaggio 7](images/Lesson5_chapter1_step7im.PNG)

8. Aggiungi una nuova risposta nel gestore di input vocale. Per eseguire questa operazione, fai clic sul pulsante "+" sottostante in cui è indicato "Response ()", contrassegnato da una freccia verde nella figura precedente.

![Immagine lezione 5 capitolo 1 passaggio 7](images/Lesson5_chapter1_step8.PNG)

9. Trascina l'oggetto con lo script Diagnostics Demo Controls (Controlli demo diagnostica) nella nuova risposta che hai appena creato nel passaggio 8.
    ![Immagine lezione 5 capitolo 1 passaggio 9](images/Lesson5_chapter1_step9im.PNG)

10. Ora seleziona l'elenco a discesa "No Function" (Nessuna funzione), seleziona i controlli demo di diagnostica e quindi "OnToggleDiagnostics ()". Questa funzione consente di attivare o disattivare la diagnostica.  ![Immagine lezione 5 capitolo 1 passaggio 10](images/Lesson5_chapter1_step10im.PNG)
    
> Tieni presente che prima di creare il dispositivo devi abilitare le impostazioni del microfono. Per eseguire questa operazione, fai clic su un file, passa alle impostazioni di compilazione, quindi alle impostazioni del lettore e verifica che la funzionalità del microfono sia impostata.

Aggiungeremo quindi la capacità di riprodurre un file audio da un comando vocale usando l'oggetto "ottaedro". Ricorderai che nella [lezione 4](mrlearning-base-ch4.md) abbiamo aggiunto la capacità di riprodurre un clip audio toccando l'oggetto ottaedro. Sfrutteremo la stessa origine audio per il comando vocale musicale.

11. Seleziona l'oggetto ottaedro nella gerarchia della scena.

12. Aggiungi un altro gestore di input vocale (ripeti i passaggi 4 e 5), ma con l'oggetto ottaedro. 

13. Invece di aggiungere il comando vocale "Toggle Diagnostics" (Attiva/Disattiva diagnostica) del passaggio 6, aggiungi il comando vocale "Play Music" (Riproduci musica), come illustrato nell'immagine seguente.
    
     ![Immagine lezione 5 capitolo 1 passaggio 13](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Come nei passaggi 8 e 9, aggiungi una nuova risposta e trascina l'ottaedro nello slot vuoto sulla risposta.

15. Seleziona il menu a discesa denominato "No Function" (Nessuna funzione), quindi "AudioSource" e infine "PlayOneShot (AudioClip)".

![Immagine lezione 5 capitolo 1 passaggio 15](images/Lesson5_chapter1_step15im.PNG)

16. Per quanto riguarda il clip audio, per questo esempio useremo lo stesso clip della [lezione 4](mrlearning-base-ch4.md). Passa al pannello del progetto, cerca il clip audio "MRTK_Gem" e trascinalo nello slot dell'origine audio, come illustrato nell'immagine seguente. A questo punto, l'applicazione dovrebbe essere in grado di rispondere ai comandi vocali "Toggle Diagnostics" (Attiva/Disattiva diagnostica) per attivare o disattivare il pannello del contatore della frequenza dei fotogrammi e "Play Music" (Riproduci musica) per riprodurre il brano MRTK_Gem.
     ![Immagine lezione 5 capitolo 1 passaggio 16](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Il movimento di panoramica 

In questo capitolo impareremo a usare il movimento di panoramica. Questo movimento è utile per le operazioni di scorrimento del contenuto (tramite il dito o la mano) e può essere usato anche per ruotare gli oggetti, scorrere una raccolta di oggetti 3D o persino scorrere un'interfaccia utente 2D. Apprenderemo come usare il movimento di panoramica per distorcere una trama. Vedremo anche come spostare una raccolta di oggetti 3D.

1. Crea un quadrilatero. Nella gerarchia della scena di base fai clic con il pulsante destro del mouse, seleziona "3D Object" (Oggetto 3D) e quindi "Quad".

![Immagine lezione 5 capitolo 2 passaggio 2](images/Lesson5_chapter2_step2im.PNG)

2. Riposiziona il quadrilatero nel modo appropriato. Per questo esempio, impostiamo x = 0, y = 0 e z = 1.5, lontano dalla videocamera per consentire una posizione comoda dal dispositivo HoloLens 2.

   > Nota: se il quadrilatero si trova in primo piano rispetto a oggetti di contenuto delle lezioni precedenti, assicurati di spostarlo per evitare che blocchi gli altri oggetti.

3. Applica un materiale al quadrilatero. Questo sarà il materiale che scorreremo con il movimento di panoramica. 

![Immagine lezione 5 capitolo 2 passaggio 3](images/Lesson5_chapter2_step3im.PNG)

4. Nel pannello del progetto digita "pan content" nella casella di ricerca. Trascina il materiale sul quadrilatero nella scena. 

> Nota: il materiale "Pan content" (Contenuto panoramica) non è disponibile in MRTK, ma è un asset incluso nel pacchetto di asset del modulo importato nelle lezioni precedenti. 

> Nota: quando aggiungi il contenuto per la panoramica, potrebbe avere un aspetto allungato. Puoi risolvere il problema modificando i valori x, y e z delle dimensioni del quadrilatero fino a ottenere l'aspetto desiderato.

Per usare il movimento di panoramica, avrai bisogno di un collisore sull'oggetto. Noterai che nel quadrilatero è già presente un collisore di tipo mesh. Tuttavia, questo tipo di collisore non è ideale, perché è estremamente sottile e difficile da selezionare. Consigliamo quindi di sostituirlo con un collisore cubico.

5. Fai clic con il pulsante destro del mouse sul collisore di tipo mesh presente nel quadrilatero (nel pannello di controllo) e rimuovilo facendo clic su "Remove Component" (Rimuovi componente). 
   ![Immagine lezione 5 capitolo 2 passaggio 5](images/Lesson5_chapter2_step5im.PNG)

6. Aggiungi ora il collisore cubico facendo clic su "Add Component" (Aggiungi componente) e cercando "box collider". Il collisore cubico predefinito è ancora troppo sottile, quindi fai clic sul pulsante "Edit Collider" (Modifica collisore) per modificarlo. Quando il pulsante è premuto, puoi regolare le dimensioni usando i valori x, y e z o gli elementi nell'editor della scena. Per questo esempio, vogliamo estendere leggermente il collisore cubico dietro il quadrilatero. Nell'editor della scena trascina il collisore cubico dal retro verso l'esterno, come illustrato nell'immagine seguente. In questo modo si consentirà all'utente di usare non solo il dito ma l'intera mano per eseguire l'azione di scorrimento. 
    ![Immagine lezione 5 capitolo 2 passaggio 6](images/Lesson5_chapter2_step6im.PNG)
7. Configura l'interattività. Poiché vogliamo interagire direttamente con il quadrilatero, decidiamo di usare il componente "Near Interaction Touchable" (Toccabile con interazione da vicino), lo stesso che abbiamo usato nella lezione 4 per riprodurre musica dall'ottaedro. Fai clic su "Add Component" (Aggiungi componente), cerca "near interaction touchable" e seleziona il componente, come illustrato nelle immagini seguenti. 

8. Aggiungi la capacità di riconoscere il movimento di panoramica. Fai clic su "Add component" (Aggiungi componente) e digita "hand interaction pan". Potrai scegliere tra Hand Ray (Raggio mano), in modo da eseguire una panoramica a distanza, e Index Finger (Dito indice). Per questo esempio, manterremo impostata la seconda opzione. 
    ![Immagine lezione 5 capitolo 2 passaggio 7 immagine 8](images/Lesson5_chapter2_step7-8im.PNG)

![Immagine lezione 5 capitolo 2 passaggio 8](images/Lesson5_chapter2_step8im.PNG)

9. Nello script Hand Interaction Pan (Panoramica con interazione manuale), le caselle di controllo "Lock Horizontal" (Blocca in orizzontale) e "Lock Vertical" (Blocca in verticale) bloccheranno i movimenti, rispettivamente in orizzontale e in verticale. Le impostazioni di Wrap texture (Avvolgi trama) consentiranno alla trama (mapping della trama) di seguire i movimenti di panoramica dell'utente. Per questo esempio, selezioneremo questa casella. È inoltre disponibile l'opzione "Velocity Active" (Attivo in base a velocità) che, se deselezionata, impedisce il movimento di panoramica. Seleziona anche questa casella. A questo punto, dovresti avere un quadrilatero abilitato per la panoramica.

   

   Imparerai ora a fare una panoramica degli oggetti 3D. 

10. Fai clic con il pulsante destro del mouse sull'oggetto Quad, seleziona 3D Object (Oggetto 3D) e quindi fai clic su "Cube". Ridimensiona il cubo in modo che assuma approssimativamente i valori x = 0.1, y = 0.1 e z = 0.1. Copia il cubo tre volte, facendo clic con il pulsante destro del mouse sul cubo e scegliendo Duplicate (Duplica) oppure premendo CTRL/Comando+D. Distanzia i cubi in modo uniforme. La scena dovrebbe avere un aspetto simile all'immagine seguente.

![Immagine lezione 5 capitolo 2 passaggio 10](images/Lesson5_chapter2_step10im.PNG)







11. Seleziona di nuovo il quadrilatero e, con lo script Hand Interaction Pan (Panoramica con interazione manuale), imposta le azioni di panoramica su ciascuno dei cubi. In "Pan Event Receivers" (Destinatari evento panoramica) specifica il numero di oggetti che ricevono l'evento. Poiché sono presenti quattro cubi, digita "4" e premi INVIO. Verranno visualizzati quattro campi vuoti.


![Immagine lezione 5 capitolo 2 passaggio 11](images/Lesson5_chapter2_step11im.PNG)



12. Trascina ciascuno dei cubi in uno degli slot di elemento vuoti.
     ![Immagine lezione 5 capitolo 2 passaggio 12](images/Lesson5_chapter2_step12im.PNG)
    
13. Aggiungi lo script "Move With Pan" (Sposta con panoramica) a tutti i cubi. Per eseguire questa operazione, tieni premuto CTRL/Comando e seleziona ogni oggetto. Nel pannello di controllo fai clic sul pulsante "Add Component" (Aggiungi componente) e cerca "move with pan". Fai clic sullo script, che verrà aggiunto a ogni cubo. Ora gli oggetti 3D si sposteranno seguendo il tuo movimento di panoramica. Se rimuovi il renderer della mesh sul quadrilatero, dovresti ottenere un quadrilatero invisibile in cui puoi fare una panoramica attraverso un elenco di oggetti 3D.

### <a name="eye-tracking"></a>Tracciamento oculare

In questo capitolo esamineremo come abilitare il tracciamento oculare nella nostra demo. Ruoteremo lentamente voci di menu 3D quando sono sotto il controllo dello sguardo fisso. Attiveremo inoltre un effetto divertente al momento della selezione dell'oggetto fissato.

1. Verifica che i profili di Mixed Reality Toolkit siano configurati correttamente. Al momento della stesura di questo documento, la configurazione dei profili di Mixed Reality Toolkit non include le funzionalità di tracciamento oculare per impostazione predefinita. Per aggiungere queste funzionalità, segui le istruzioni nella sezione "Configurazione dei profili di MRTK necessari per il tracciamento oculare" nella [documentazione di Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Assicurati che il tracciamento oculare sia configurato correttamente eseguendo i passaggi rimanenti nella pagina visualizzata tramite il precedente collegamento alla documentazione, incluse l'abilitazione del tracciamento oculare in GazeProvider (componente collegato alla videocamera) e l'abilitazione della simulazione del tracciamento oculare nell'editor di Unity. Tieni presente che la versione futura di MRTK potrebbe includere le funzionalità di tracciamento oculare per impostazione predefinita.

    Il collegamento precedente consente di accedere a brevi istruzioni per:

    - Creare un provider di dati per lo sguardo fisso da usare nel profilo di MRTK
    - Abilitare il tracciamento oculare nel provider di dati per lo sguardo fisso
    - Definire la configurazione per simulare il tracciamento oculare nell'editor
    - Modificare le funzionalità della soluzione Visual Studio per consentire il tracciamento oculare nell'applicazione compilata

2. Aggiungi il componente Eye Tracking Target (Destinazione tracciamento oculare) agli oggetti di destinazione. Per consentire a un oggetto di rispondere agli eventi dello sguardo fisso, dobbiamo aggiungere questo componente a ogni oggetto con cui vogliamo interagire usando lo sguardo. Aggiungi questo componente a ciascuno dei nove oggetti 3D che fanno parte della raccolta griglia. Suggerimento: seleziona più elementi nella gerarchia per aggiungere in blocco il componente Eye Tracking Target (Destinazione tracciamento oculare).
    ![Lezione 5 capitolo 3 passaggio 2](images/Lesson5Chapter3Step2.JPG)

3. A questo punto aggiungeremo lo script EyeTrackingTutorialDemo per alcune interessanti interazioni. Questo script è incluso nel repository di questa serie di esercitazioni e non è disponibile per impostazione predefinita in Mixed Reality Toolkit. Per ogni oggetto 3D nella raccolta griglia, aggiungi lo script EyeTrackingTutorialDemo eseguendo una ricerca del componente nel menu "Add Component" (Aggiungi componente).
   ![Lezione 5 capitolo 3 passaggio 3](images/Lesson5Chapter3Step3.JPG)

   4. Configura l'oggetto in modo da ruotare mentre il tuo sguardo è rivolto verso la destinazione. Vogliamo ora configurare un oggetto 3D in modo da ruotare mentre lo stiamo fissando. Per eseguire questa operazione, inserisci un nuovo campo nella sezione "While Looking At Target" (Sguardo verso la destinazione) del componente Eye Tracking Target (Destinazione tracciamento oculare), come illustrato nell'immagine seguente. 

![Lezione 5 capitolo 3 passaggio 4a](images/Lesson5Chapter3Step4a.JPG)
![Lezione 5 capitolo 3 passaggio 4b](images/Lesson5Chapter3Step4b.JPG)



Nel campo appena creato, aggiungi l'oggetto gioco corrente nel campo vuoto e seleziona EyeTrackingTutorialDemo > RotateTarget(), come illustrato nell'immagine seguente. L'oggetto 3D è ora configurato in modo da ruotare quando viene fissato con il tracciamento oculare. 

5. Aggiungi ora una funzione per far lampeggiare la destinazione quando viene fissata al momento della selezione (tramite simulazione del tocco o con il comando vocale "select"). In modo analogo al passaggio 4, attiva EyeTrackingTutorialDemo > BlipTarget() assegnando questa funzione al campo "Select()" dell'oggetto gioco del componente Eye Tracking Target (Destinazione tracciamento oculare), come illustrato nella figura seguente. Con questa configurazione, noterai un lieve lampeggiamento dell'oggetto gioco ogni volta che attiverai un'azione di selezione, ad esempio tramite simulazione del tocco o con il comando vocale "select". 
    ![Lezione 5 capitolo 3 passaggio 5](images/Lesson5Chapter3Step5.JPG)
6. Verifica che le funzionalità di tracciamento oculare siano configurate correttamente prima di compilarle in HoloLens 2. Al momento della stesura di questo documento, in Unity non è ancora possibile impostare la funzionalità di input dello sguardo fisso (per il tracciamento oculare). L'impostazione di questa funzionalità è necessaria per il funzionamento del tracciamento oculare su HoloLens 2. Per abilitare la funzionalità di input dello sguardo fisso, segui queste istruzioni nella documentazione di Mixed Reality Toolkit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>A questo punto, 
Hai ora aggiunto all'applicazione le funzionalità di base per il tracciamento oculare. Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare. Con questo capitolo si conclude anche la lezione 5, in cui hai imparato a usare funzionalità di input avanzate, come i comandi vocali, i movimenti di panoramica e il tracciamento oculare. 

[Lezione successiva: Esperienza di esempio di assemblaggio di un modulo lunare](mrlearning-base-ch6.md)

