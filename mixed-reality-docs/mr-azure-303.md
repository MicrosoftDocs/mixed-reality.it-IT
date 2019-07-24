---
title: MR e Azure 303-LUIS (Natural Language Understanding)
description: Completare questo corso per apprendere come implementare Azure Language Understanding Intelligence Service (LUIS) in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Language Understanding Intelligence Service, Luis, hololens, immersive, VR
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63555159"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR e Azure 303: LUIS (Natural Language Understanding)

In questo corso si apprenderà come integrare Language Understanding in un'applicazione di realtà mista usando servizi cognitivi di Azure, con il API Language Understanding.

![risultato Lab](images/AzureLabs-Lab3-000.png)

*Language Understanding (Luis)* è un servizio di Microsoft Azure, che offre alle applicazioni la possibilità di rendere il significato fuori dall'input dell'utente, ad esempio tramite l'estrazione di ciò che un utente potrebbe desiderare, nelle proprie parole. Questa operazione viene eseguita tramite Machine Learning, che comprende e apprende le informazioni di input e quindi può rispondere con informazioni dettagliate, pertinenti. Per ulteriori informazioni, visitare la [pagina Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Acquisire la voce di input dell'utente, usando il microfono collegato alla cuffia ad immersiva. 
2.  Inviare la dettatura acquisita ad *Azure Language Understanding Intelligent Service* (*Luis*). 
3.  Ottenere il significato di LUIS Extract dalle informazioni di invio, che verranno analizzate e verrà effettuato un tentativo di determinare lo scopo della richiesta dell'utente.

Lo sviluppo includerà la creazione di un'app in cui l'utente potrà usare la voce e/o lo sguardo per modificare le dimensioni e il colore degli oggetti nella scena. L'uso dei controller di movimento non verrà analizzato.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

Prepararsi a eseguire il training di LUIS più volte, come spiegato nel [capitolo 12](#chapter-12--improving-your-luis-service). Si otterranno risultati migliori più volte che LUIS è stato sottoposto a training.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR e Azure 303: LUIS (Natural Language Understanding)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md)
- [Windows 10 SDK più recente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)
- Accesso a Internet per il programma di installazione di Azure e il recupero LUIS

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione). 
2.  Per consentire al computer di abilitare la dettatura, passare a **impostazioni di Windows > Privacy > vocale, Inking &** digitando e premere il pulsante **Attiva servizi vocali e digitando suggerimenti**.
3.  Il codice in questa esercitazione consentirà di registrare dal set di **dispositivi del microfono predefinito** nel computer. Verificare che il dispositivo microfonico predefinito sia impostato come quello che si vuole usare per acquisire la voce.
4.  Se la cuffia ha un microfono incorporato, assicurarsi che l'opzione *"quando si indossa la cuffia, passa alla cuffia auricolare"* sia attivata nelle impostazioni del portale per la *realtà mista* .

    ![Configurazione dell'auricolare immersivo](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capitolo 1: configurare il portale di Azure

Per usare il servizio *Language Understanding* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.

1.  Accedere al [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *Language Understanding*e premere **invio**. 

    ![Crea risorsa LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.
 
3.  La nuova pagina a destra fornirà una descrizione del servizio Language Understanding. Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'istanza di questo servizio.

    ![Creazione del servizio LUIS-note legali](images/AzureLabs-Lab3-02.png)
 
4.  Una volta fatto clic su Crea:

    1. Inserire il **nome** desiderato per l'istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Selezionare il  piano tariffario appropriato. se è la prima volta che si crea un *servizio Luis*, è necessario che sia disponibile un livello gratuito (denominato F0). L'allocazione gratuita dovrebbe essere più che sufficiente per questo corso.
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    6. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.
    7. Selezionare **Create**.

        ![Crea servizio LUIS-input utente](images/AzureLabs-Lab3-03.png)
 
5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.
6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale. 
 
    ![Nuova immagine di notifica di Azure](images/AzureLabs-Lab3-04.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Notifica di creazione risorse riuscita](images/AzureLabs-Lab3-05.png)
 
8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio LUIS. 
 
    ![Accesso alle chiavi LUIS](images/AzureLabs-Lab3-06.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio.
10. Dalla pagina *avvio rapido* , del servizio *API Luis* , passare al primo passaggio, recuperare *le chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti collegamento ipertestuale blu, che si trovano nel menu di navigazione servizi, indicato da icona della chiave). Le *chiavi*del servizio vengono rivelate.
11. Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto. 
12. Nella pagina del *servizio* fare clic su *Language Understanding portale* per essere reindirizzati alla pagina Web che verrà usata per creare il nuovo servizio, all'interno dell'app Luis. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capitolo 2: portale di Language Understanding

In questa sezione si apprenderà come creare un'app LUIS nel portale LUIS. 

> [!IMPORTANT]
> Tenere presente che la configurazione di *entità* *, finalità*ed *espressioni* in questo capitolo è solo il primo passaggio per la creazione del servizio Luis: è anche necessario ripetere il training del servizio, più volte, in modo da renderlo più accurato. La ripetizione del training del servizio è trattata nell' [ultimo capitolo](#chapter-12--improving-your-luis-service) di questo corso, quindi è necessario verificarne il completamento.

1.  Quando si raggiunge il *portale di Language Understanding*, potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure. 

    ![Pagina di accesso LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se è la prima volta che si usa LUIS, sarà necessario scorrere verso il basso fino alla fine della pagina iniziale per trovare e fare clic sul pulsante **create Luis app** .

    ![Pagina Crea app LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Una volta effettuato l'accesso, fare clic su **app personali** (se non si è attualmente in questa sezione). È quindi possibile fare clic su **Crea nuova app**.

    ![Immagine di LUIS-My Apps](images/AzureLabs-Lab3-09.png)
 
4.  Assegnare un *nome*all'app.
5.  Se l'app dovrebbe comprendere una lingua diversa dall'inglese, è necessario modificare le *impostazioni cultura* in base alla lingua appropriata.
6.  Qui è anche possibile aggiungere una *Descrizione* della nuova app Luis.

    ![LUIS-crea una nuova app](images/AzureLabs-Lab3-10.png)

7.  Una volta fatto clic su **fine**, si passerà alla pagina *Compila* della nuova applicazione *Luis* .
8.  Ecco alcuni concetti importanti da comprendere:

    -   *Intent*, rappresenta il metodo che verrà chiamato dopo una query dall'utente. Una *finalità* può includere una o più *entità*.
    -   *Entity*, è un componente della query che descrive le informazioni relative allo *scopo*.
    -   Le *espressioni*sono esempi di query fornite dallo sviluppatore, che Luis utilizzerà per eseguire il training.

Se questi concetti non sono perfettamente chiari, non preoccuparti, perché in questo corso verranno chiariti più avanti in questo capitolo.

Si inizierà creando le *entità* necessarie per compilare questo corso.

9.  Sul lato sinistro della pagina fare clic su *entità*e quindi su **Crea nuova entità**.

    ![Crea nuova entità](images/AzureLabs-Lab3-11.png)

10. Chiamare il nuovo *colore*dell'entità, impostarne il tipo su *Simple*, quindi fare clic su **done**.

    ![Crea entità-colore semplice](images/AzureLabs-Lab3-12.png)
 
11. Ripetere questo processo per creare tre (3) entità più semplici denominate:

    -   *Upsize*
    -   *ridimensionare*
    -   *destinazione*

Il risultato dovrebbe essere simile all'immagine seguente:

![Risultato della creazione di entità](images/AzureLabs-Lab3-13.png)
 
A questo punto è possibile iniziare la creazione di Intent. 

> [!WARNING]
> Non eliminare la finalità **None** .

12. Sul lato sinistro della pagina fare clic su Intent , quindi fare clic su **Crea nuovo scopo**.

    ![Crea nuovi Intent](images/AzureLabs-Lab3-14.png)

13. Chiamare la nuova *finalità* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Questo nome di *finalità* viene usato all'interno del codice più avanti in questo corso. per ottenere risultati ottimali, usare questo nome esattamente come fornito.

Dopo aver confermato il nome, si verrà indirizzati alla pagina Intent.

![Pagina LUIS-Intent](images/AzureLabs-Lab3-15.png)

Si noterà che è presente una casella di testo in cui viene chiesto di digitare 5 o più *espressioni*diverse.

> [!NOTE]
> LUIS converte tutti gli enunciati in lettere minuscole.

14. Inserire l' *espressione* seguente nella casella di testo top (attualmente con il *tipo di testo circa 5 esempi...* ) e premere **invio**:

```
The color of the cylinder must be red
```

Si noterà che il nuovo *enunciato* verrà visualizzato in un elenco sottostante.

Seguendo lo stesso processo, inserire le sei (6) espressioni seguenti:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Per ogni espressione creata è necessario identificare le parole che devono essere usate da LUIS come entità. In questo esempio è necessario etichettare tutti i colori come entità di *colore* e il riferimento possibile a una destinazione come entità di *destinazione* .

15. A tale scopo, provare a fare clic sulla parola *Cylinder* nel primo enunciatore e selezionare *destinazione*.

    ![Identificare le destinazioni di espressione](images/AzureLabs-Lab3-16.png)
 
16. A questo punto, fare clic sulla parola *rosso* nel primo enunciato e selezionare *colore*.

    ![Identificare le entità enunciate](images/AzureLabs-Lab3-17.png)
 
17. Etichettare anche la riga successiva, dove *Cube* deve essere una *destinazione*e il *nero* deve essere un *colore*. Si noti anche l'uso delle parole *' This '* , *' it '* e *' This object '* , che vengono fornite, in modo da rendere disponibili anche tipi di destinazione non specifici. 

18. Ripetere il processo precedente fino a quando non sono presenti le entità etichettate per tutte le espressioni. Se è necessaria assistenza, vedere l'immagine seguente.

    > [!TIP]
    > Quando si selezionano le parole per etichettarle come entità:
    > - Per le singole parole, basta fare clic su di essi.
    > - Per un set di due o più parole, fare clic all'inizio, quindi alla fine del set.

    > [!NOTE]
    > È possibile usare l'interruttore di *visualizzazione token* per passare dalla **visualizzazione entità/token**.

19. I risultati dovrebbero essere come illustrato nelle immagini seguenti, mostrando la **visualizzazione entità/token**:

    ![Token & viste entità](images/AzureLabs-Lab3-18.png)
  
20. A questo punto, fare clic sul pulsante di **Train** nella parte superiore destra della pagina e attendere che il piccolo indicatore rotondo venga trasformato in verde. Indica che LUIS è stato sottoposto a training per riconoscere questa finalità.

    ![Train LUIS](images/AzureLabs-Lab3-19.png)
 
21. Come esercizio, creare una nuova finalità denominata **ChangeObjectSize**, usando la *destinazione*delle entità, le *dimensioni*e il ridimensionamento .
22. Seguendo lo stesso processo dell'intento precedente, inserire i seguenti otto (8) espressioni per la modifica delle *dimensioni* :

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. Il risultato dovrebbe essere simile a quello dell'immagine seguente:

    ![Configurare i token/entità di ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Una volta creati e sottoposti a training entrambi gli Intent, **ChangeObjectColor** e **ChangeObjectSize**, fare clic sul pulsante **pubblica** nella parte superiore della pagina.

    ![Pubblica servizio LUIS](images/AzureLabs-Lab3-21.png)

25. Nella pagina *pubblica* verrà finalizzata e pubblicata l'app Luis in modo che possa accedere al codice.

    1. Impostare la casella *di riepilogo a discesa pubblica su* come **produzione**.
    2. Impostare il *fuso orario* sul fuso orario.
    3. Selezionare la casella **Includi tutti i punteggi della finalità stimati**.
    4. Fare clic su **pubblica in slot di produzione**.

        ![Impostazioni di pubblicazione](images/AzureLabs-Lab3-22.png)

26. Nella sezione *risorse e chiavi*:

    1.  Selezionare l'area impostata per l'istanza del servizio nel portale di Azure.
    2.  Si noterà un elemento **Starter_Key** di seguito, che verrà ignorato.
    3.  Fare clic su **Aggiungi chiave** e inserire la *chiave* ottenuta nel portale di Azure al momento della creazione dell'istanza del servizio. Se il portale di Azure e il portale LUIS sono connessi allo stesso utente, verranno forniti menu a discesa per *nome tenant*, *nome sottoscrizione*e *chiave* che si vuole usare (avrà lo stesso nome fornito in precedenza nel portale di Azure.

    > [!IMPORTANT] 
    > Sotto l' *endpoint*, eseguire una copia dell'endpoint corrispondente alla chiave inserita, che verrà a breve usata nel codice.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capitolo 3: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab3-24.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity, inserire **MR_LUIS**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a Modifica Preferenze > e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab3-26.png)
 
4.  Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Passare a **File > impostazioni di compilazione** e verificare che:

    1. Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2. Il **tipo di compilazione** è impostato su **D3D**
    3. **SDK** è impostato sull' **ultima versione installata**
    4. La **versione di Visual Studio** è impostata su **installazione più recente**
    5. **Compilazione ed esecuzione** è impostato su **computer locale**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab3-28.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![Crea nuova cartella script](images/AzureLabs-Lab3-29.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_LuisScene**e quindi fare clic su **Salva**.

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab3-30.png)

    7. Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

6. Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab3-31.png) 
 
7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1. La **versione di runtime** di scripting deve essere **stabile** (equivalente a .NET 3,5).
        2. Il **back-end** di scripting deve essere **.NET**
        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab3-32.png)
      
    2. Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab3-33.png)

    3. Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab3-34.png)

8.  Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra impostazioni di compilazione.
10. Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).

## <a name="chapter-4--create-the-scene"></a>Capitolo 4: creare la scena

> [!IMPORTANT]
> Se si desidera ignorare il componente *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **piano**.

    ![Creare un piano.](images/AzureLabs-Lab3-35.png)

2.  Tenere presente che quando si fa di nuovo clic con il pulsante destro del mouse all'interno della *gerarchia* per creare più oggetti, se è ancora stato selezionato l'ultimo oggetto, l'oggetto selezionato sarà l'elemento padre del nuovo oggetto. Per evitare questo problema, fare clic con il pulsante destro del mouse su uno spazio vuoto all'interno della gerarchia.

3.  Ripetere la procedura precedente per aggiungere gli oggetti seguenti:

    1. *Sfera*
    2. *Cilindro*
    3. *Cubo*
    4. *Testo 3D*

4.  La *gerarchia* della scena risultante deve essere simile a quella dell'immagine seguente:

    ![Impostazione della gerarchia della scena.](images/AzureLabs-Lab3-36.png)
 
5.  Fare clic sulla **fotocamera principale** per selezionarla. esaminare il *pannello Inspector* per visualizzare l'oggetto fotocamera con tutti i relativi componenti.
6.  Fare clic sul pulsante **Aggiungi componente** che si trova nella parte inferiore del *pannello Inspector*.

    ![Aggiungi origine audio](images/AzureLabs-Lab3-37.png)
 
7.  Cercare il componente denominato *origine audio*, come illustrato in precedenza.
8.  Assicurarsi inoltre che il componente *trasformazione* della fotocamera principale sia impostato su (0, 0, 0). a tale scopo, è possibile premere l'icona a forma di ingranaggio accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**. Il componente *Transform* dovrebbe essere simile al seguente:

    1.  *Position* è impostato su **0, 0, 0**.
    2.  *Rotation* è impostato su **0, 0, 0**.

    > [!NOTE] 
    > Per Microsoft HoloLens, è necessario modificare anche quanto segue, che fa parte del componente della **fotocamera** , presente nella **fotocamera principale**:
    > - **Cancella flag:** Colore a tinta unita.
    > - **Informazioni preliminari** ' Black, Alpha 0'-colore esadecimale: #00000000.

9.  Fare clic sul **piano** per selezionarlo. Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:

    |       | Trasformazione- *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. Fare clic sulla **sfera** per selezionarla. Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:

    |       | Trasformazione- *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. Fare clic sul **cilindro** per selezionarlo. Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:

    |       | Trasformazione- *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2    | 1                      | 2     |

12. Fare clic sul **cubo** per selezionarlo. Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:

    |        | Trasformazione- *posizione* |       |  \| |       | Trasformazione- *rotazione* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Fare clic sul **nuovo oggetto testo** per selezionarlo. Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:

    |       | Trasformazione- *posizione* |       |  \| |       | Trasformazione- *Ridimensiona* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | 2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Modificare le **dimensioni del carattere** nel componente mesh di **testo** in **50**.
15. Modificare il *nome* dell'oggetto **mesh di testo** in **testo**di dettatura.

    ![Crea oggetto testo 3D](images/AzureLabs-Lab3-38.png)
 
16. La struttura del pannello della gerarchia dovrebbe ora essere simile alla seguente:

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab3-38b.png)


17. La scena finale dovrebbe essere simile all'immagine seguente:

    ![Visualizzazione della scena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capitolo 5: creare la classe MicrophoneManager

Il primo script che si intende creare è la classe *MicrophoneManager* . A questo punto si creeranno i *LuisManager*, la  classe Behaviors e infine la classe *sguardi* (è possibile crearli tutti ora, anche se verranno trattati quando si raggiunge ogni capitolo).

La classe *MicrophoneManager* è responsabile di:

-   Rilevamento del dispositivo di registrazione collegato all'auricolare o al computer (a seconda del valore predefinito).
-   Acquisire l'audio (voce) e utilizzare la dettatura per archiviarlo come stringa.
-   Una volta sospesa la voce, inviare la dettatura alla classe *LuisManager* . 

Per creare questa classe: 

1.  Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**. Chiamare gli **script**della cartella. 

    ![Crea cartella script.](images/AzureLabs-Lab3-40.png)
 
2.  Con la  cartella Scripts creata, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse su **Crea Script > C#** . Denominare lo script *MicrophoneManager*. 

3.  Fare doppio clic su *MicrophoneManager* per aprirlo con *Visual Studio*.
4.  Aggiungere i seguenti spazi dei nomi all'inizio del file:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *MicrophoneManager* :

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* . Questi verranno chiamati quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  A questo punto è necessario il metodo che l'app usa per avviare e arrestare l'acquisizione vocale e passarla alla classe *LuisManager* , che verrà compilata a breve. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Aggiungere un *gestore* di dettatura che verrà richiamato quando la voce viene sospesa. Questo metodo passerà il testo della dettatura alla classe *LuisManager* .

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare il metodo *Update ()* perché non verrà utilizzato da questa classe.

9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

    > [!NOTE]
    > A questo punto si noterà un errore nel *Pannello console dell'editor*di Unity. Questo perché il codice fa riferimento alla classe *LuisManager* che verrà creata nel capitolo successivo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capitolo 6: creare la classe LUISManager

È il momento di creare la classe *LuisManager* , che effettuerà la chiamata al servizio Azure Luis. 

Lo scopo di questa classe è di ricevere il testo della dettatura dalla classe *MicrophoneManager* e di inviarlo al *API Language Understanding di Azure* da analizzare.

Questa classe deserializzare la risposta *JSON* e chiamare i metodi appropriati della classe *behaviors* per attivare un'azione.

Per creare questa classe: 

1.  Fare doppio clic sulla  cartella Scripts per aprirla. 
2.  Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare lo script *LuisManager*. 
3.  Fare doppio clic sullo script per aprirlo con Visual Studio.
4.  Aggiungere i seguenti spazi dei nomi all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Si inizierà creando tre classi **all'interno** della classe *LuisManager* (all'interno dello stesso file di script, sopra il metodo *Start ()* ) che rappresenterà la risposta JSON deserializzata da Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Aggiungere quindi le variabili seguenti all'interno della classe *LuisManager* :
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Assicurarsi di inserire l'endpoint LUIS in ora, che sarà disponibile nel portale LUIS.

8.  È ora necessario aggiungere il codice per il metodo *svegli ()* . Questo metodo verrà chiamato quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  A questo punto sono necessari i metodi usati da questa applicazione per inviare la dettatura ricevuta dalla classe *MicrophoneManager* a *Luis*, quindi ricevere e deserializzare la risposta. 
10. Una volta che il valore dello scopo e le entità associate sono stati determinati, vengono passati all'istanza della classe Behaviors  per attivare l'azione desiderata.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Creare un nuovo metodo denominato *AnalyseResponseElements ()* in grado di leggere il *AnalysedQuery* risultante e determinare le entità. Una volta determinate tali entità, verranno passate all'istanza della classe Behaviors da  usare nelle azioni.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare i metodi *Start ()* e *Update ()* perché questa classe non li utilizzerà.

12. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

> [!NOTE]
> A questo punto si noterà che nel *Pannello console dell'editor*di Unity verranno visualizzati diversi errori. Questo perché il codice fa riferimento alla  classe behaviors che verrà creata nel capitolo successivo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capitolo 7: creare la classe Behaviors

La  classe Behaviors attiverà le azioni usando le entità fornite dalla classe *LuisManager* .

Per creare questa classe: 

1.  Fare doppio clic sulla  cartella Scripts per aprirla. 
2.  Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Assegnare un nome ai *comportamenti*dello script. 
3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.
4.  Aggiungere quindi le variabili seguenti all'interno  della classe Behaviors:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Aggiungere il codice del metodo *sveglie ()* . Questo metodo verrà chiamato quando la classe inizializza:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  I metodi seguenti vengono chiamati dalla classe *LuisManager* (creata in precedenza) per determinare quale oggetto è la destinazione della query e quindi attivare l'azione appropriata.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Aggiungere il metodo *FindTarget ()* per determinare quale *GameObject* è la destinazione dello scopo corrente. Questo metodo imposta come valore predefinito la destinazione per *GameObject* che viene "guardato" se nelle entità non è definita alcuna destinazione esplicita.

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Eliminare i metodi *Start ()* e *Update ()* perché questa classe non li utilizzerà.

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capitolo 8-creare la classe sguardi

L'ultima classe che sarà necessario completare questa app è la classe *sguardi* . Questa classe aggiorna il riferimento a *GameObject* attualmente nello stato attivo visivo dell'utente.

Per creare questa classe: 

1.  Fare doppio clic sulla  cartella Scripts per aprirla. 
2.  Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare *lo script.* 
3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.
4.  Inserire il codice seguente per questa classe:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Capitolo 9: completamento della configurazione della scena

1.  Per completare l'installazione della scena, trascinare ogni script creato dalla cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.
2.  Selezionare la **fotocamera principale** ed esaminare il *pannello Inspector*. dovrebbe essere possibile visualizzare ogni script collegato e si noterà che sono presenti parametri per ogni script che è ancora necessario impostare.

    ![Impostazione delle destinazioni di riferimento per la fotocamera.](images/AzureLabs-Lab3-41.png)

3.  Per impostare correttamente questi parametri, attenersi alle istruzioni seguenti:

    1. *MicrophoneManager*:

        - Dal *Pannello gerarchia*trascinare l'oggetto **testo** di dettatura nella casella valore parametro **testo** di dettatura.

    2. *Comportamenti*, dal *Pannello gerarchia*:

        - Trascinare l'oggetto **Sphere** nella casella destinazione riferimento a *sfera* .
        - Trascinare il **cilindro** nella casella destinazione riferimento *cilindro* .
        - Trascinare il **cubo** nella casella destinazione riferimento *cubo* .

    3. *Sguardo*:

        - Imposta la *distanza massima di sguardi* su **300** (se non è già presente). 

4.  Il risultato dovrebbe essere simile all'immagine seguente:

    ![Visualizzazione delle destinazioni di riferimento della fotocamera, ora impostate.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capitolo 10: eseguire il test nell'editor di Unity

Verificare che l'installazione della scena sia implementata correttamente.

Assicurarsi che:

-   Tutti gli script sono collegati all'oggetto **principale della fotocamera** . 
-   Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.

1.  Premere il pulsante **Play** nell' *Editor*di Unity. L'app deve essere in esecuzione all'interno dell'auricolare immersivo collegato.

2.  Provare alcune espressioni, ad esempio:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se nella console di Unity viene visualizzato un errore relativo alla modifica del dispositivo audio predefinito, è possibile che la scena non funzioni come previsto. Questo è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per le cuffie che li hanno. Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e le operazioni dovrebbero funzionare come previsto.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capitolo 11: compilare e sideload la soluzione UWP

Dopo aver verificato che l'applicazione funzioni nell'editor di Unity, è possibile eseguire la compilazione e la distribuzione.

Per compilare:

1.  Salvare la scena corrente facendo clic su **File > Salva**.
2.  Passare a **File > impostazioni di compilazione**.
3.  Seleziona la casella denominata **progetti C# Unity** (utile per visualizzare ed eseguire il debug del codice una volta creato il progetto UWP.
4.  Fare clic su **Aggiungi scene aperte**, quindi fare clic su **Compila**.

    ![Finestra impostazioni di compilazione](images/AzureLabs-Lab3-43.png)

4.  Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione. 

5.  Creare una  cartella compilazioni e all'interno di tale cartella creare un'altra cartella con un nome appropriato. 
6.  Fare clic su **Seleziona cartella** per iniziare la compilazione in quel percorso.
 
    ![Crea cartella](images/AzureLabs-Lab3-44.png)
    ![compilazioni selezionare la cartella compilazioni](images/AzureLabs-Lab3-45.png)
 
7.  Al termine della compilazione di Unity (potrebbe richiedere del tempo), dovrebbe aprire una finestra di **Esplora file** nel percorso della compilazione.

Per eseguire la distribuzione nel computer locale:

1.  In *Visual Studio*aprire il file di soluzione creato nel [capitolo precedente](#chapter-10--test-in-the-unity-editor).
2.  Nella **piattaforma soluzione**selezionare **x86**, **computer locale**.
3.  Nella **configurazione della soluzione** selezionare **debug**.

    > Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer. Tuttavia, sarà necessario eseguire anche le operazioni seguenti:
    > - Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.

    ![Distribuisci app](images/AzureLabs-Lab3-46.png)
 
4.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.
5.  L'app verrà visualizzata nell'elenco delle app installate, pronta per l'avvio.
6.  Una volta avviata, l'app richiederà di autorizzare l'accesso al _microfono_. Usare i *controller di movimento*o l' *input vocale*o la *tastiera* per premere il pulsante **Sì** . 

## <a name="chapter-12--improving-your-luis-service"></a>Capitolo 12: miglioramento del servizio LUIS

>[!IMPORTANT] 
> Questo capitolo è estremamente importante e potrebbe essere necessario Interated più volte, in quanto consente di migliorare l'accuratezza del servizio LUIS: assicurarsi di completare questa operazione.

Per migliorare il livello di comprensione fornito da LUIS, è necessario acquisire nuove espressioni e usarle per ripetere il training dell'app LUIS.

Ad esempio, è possibile che sia stato eseguito il training di LUIS per comprendere "aumento" e "ridimensionamento", ma non si vuole che l'app includa anche parole come "ingrandire"?

Una volta che l'applicazione è stata usata più volte, tutto ciò che si è detto verrà raccolto da LUIS e sarà disponibile nel portale LUIS.

1.  Passare all'applicazione del portale dopo questo [collegamento](https://www.luis.ai/home)ed eseguire l'accesso.
2.  Dopo aver eseguito l'accesso con le credenziali MS, fare clic sul *nome dell'app*.
3.  Fare clic sul pulsante **Verifica espressioni endpoint** a sinistra della pagina.

    ![Esaminare le espressioni](images/AzureLabs-Lab3-47.png)
 
4.  Verrà visualizzato un elenco di espressioni inviate a LUIS dall'applicazione per realtà mista.

    ![Elenco di espressioni](images/AzureLabs-Lab3-48.png)
 
Si noteranno alcune *entità*evidenziate. 

Passando il mouse su ogni parola evidenziata, è possibile esaminare ogni espressione e determinare quale entità è stata riconosciuta correttamente, quali entità sono errate e quali entità mancano.

Nell'esempio precedente, è stato rilevato che la parola "Spear" era stata evidenziata come destinazione, quindi è necessario correggere l'errore, eseguendo il passaggio del mouse sulla parola con il mouse e scegliendo **Rimuovi etichetta**.

![Controllare le espressioni](images/AzureLabs-Lab3-49.png)
![Rimuovi immagine etichetta](images/AzureLabs-Lab3-50.png)
 
5.  Se si trovano espressioni completamente errate, è possibile eliminarle usando il pulsante **Elimina** sul lato destro dello schermo.

    ![Elimina espressioni non corrette](images/AzureLabs-Lab3-51.png)

6.  In alternativa, se si ritiene che LUIS abbia interpretato correttamente l'espressione, è possibile convalidarne la comprensione usando il pulsante **Aggiungi a scopo** allineato.

    ![Aggiungi a finalità allineata](images/AzureLabs-Lab3-52.png)

7.  Una volta ordinate tutte le espressioni visualizzate, provare a ricaricare la pagina per verificare se sono disponibili ulteriori informazioni.
8.  È molto importante ripetere questo processo il maggior numero di volte possibile per migliorare la comprensione dell'applicazione. 

**Buon divertimento!**

## <a name="your-finished-luis-integrated-application"></a>Applicazione integrata LUIS completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Azure Language Understanding Intelligence, per comprendere cosa dice un utente e agire su tali informazioni.

![risultato Lab](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Quando si usa questa applicazione è possibile notare che, se si osserva l'oggetto Floor e si chiede di modificarne il colore, questa operazione verrà eseguita. È possibile risolvere il modo in cui arrestare l'applicazione modificando il colore del piano?

### <a name="exercise-2"></a>Esercizio 2

Provare a estendere le funzionalità di LUIS e app, aggiungendo funzionalità aggiuntive per gli oggetti nella scena. è ad esempio possibile creare nuovi oggetti in corrispondenza del punto di riscontro, a seconda di ciò che viene indicato dall'utente e quindi usare tali oggetti insieme agli oggetti scena correnti, con i comandi esistenti. 
