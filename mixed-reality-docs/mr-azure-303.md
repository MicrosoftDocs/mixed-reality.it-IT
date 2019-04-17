---
title: MR e Azure 303 - linguaggio naturale, comprensione (LUIS)
description: Completare questo corso di informazioni su come implementare Azure Intelligence servizio LUIS (Language Understanding) all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, servizio di intelligence language understanding, luis, hololens, vr immersivi,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603075"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR e Azure 303: Naturale LUIS (language understanding)

In questo corso, si apprenderà come integrare un'applicazione di realtà mista con servizi cognitivi di Azure, con l'API di Language Understanding Language Understanding Intelligent Service.

![risultato di Lab](images/AzureLabs-Lab3-000.png)

*LUIS (Language Understanding)* è un servizio di Microsoft Azure, che offre alle applicazioni grazie alla possibilità di rendere significato all'esterno di input dell'utente, ad esempio tramite l'estrazione di ciò che potrebbe essere una persona, opinione. Questo risultato viene ottenuto tramite machine learning, che riconosce e apprende le informazioni di input e quindi possono rispondere con informazioni dettagliate rilevanti. Per altre informazioni, visitare il [pagina Azure LUIS (Language Understanding)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:

1.  Acquisire il riconoscimento vocale input utente, usare il microfono collegato al visore VR immersivi. 
2.  Inviare la dettatura acquisita la *Azure Language Understanding Intelligent Service* (*LUIS*). 
3.  Disporre di estrazione LUIS vale a dire dalle informazioni di trasmissione, che verranno analizzate e tentano di determinare che lo scopo della richiesta dell'utente verrà apportato.

Lo sviluppo include la creazione di un'app in cui l'utente sarà in grado di usare la forma e/o estasiati per modificare le dimensioni e il colore degli oggetti nella scena. Non verrà descritto l'utilizzo di controller di movimento.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

Essere preparati a LUIS Train più volte, illustrata nel [capitolo 12](#chapter-12--improving-your-luis-service). Si otterranno risultati migliori di altre volte che LUIS è stato eseguito il training.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR e Azure 303: Naturale LUIS (language understanding)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md)
- [La versione più recente di Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Le cuffie con un microfono incorporato (se le cuffie non è presente un mic incorporati e altri relatori)
- Accesso a Internet per la configurazione di Azure e il recupero di LUIS

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione). 
2.  Per consentire la macchina per abilitare la dettatura, passare a **delle impostazioni di Windows > Privacy > vocale, input penna e digitando** e premere il pulsante **Turn On servizi di riconoscimento vocale e i suggerimenti di digitazione**.
3.  Il codice in questa esercitazione sarà possibile registrare dal **Default Device microfono** impostata nel computer. Assicurarsi che il dispositivo di microfono predefinito viene impostato come quello che si desidera usare per acquisire la voce dell'utente.
4.  Se le cuffie dispone di un microfono incorporato, assicurarsi che l'opzione *"Quando wear my le cuffie, passare a microfono auricolare"* attivata nel *portale di realtà mista* impostazioni.

    ![Configurazione di visore VR immersivi](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capitolo 1: configurare il portale di Azure

Usare la *Language Understanding Intelligent Service* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.

1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *Language Understanding Intelligent Service*, fare clic su **invio**. 

    ![Crea risorsa di LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.
 
3.  La nuova pagina a destra fornirà una descrizione del servizio Language Understanding Intelligent Service. AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'istanza di questo servizio.

    ![Creazione di un servizio LUIS - note legali](images/AzureLabs-Lab3-02.png)
 
4.  Dopo avere fatto clic su Crea:

    1. Inserire la posizione desiderata **nome** per questa istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *LUIS Service*, un livello gratuito, denominato F0, debba essere disponibile. L'allocazione gratuito deve essere più che sufficiente per questo corso.
    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    6. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.
    7. Selezionare **Create**.

        ![Crea servizio LUIS - input dell'utente](images/AzureLabs-Lab3-03.png)
 
5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.
6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale. 
 
    ![Nuova immagine di notifica di Azure](images/AzureLabs-Lab3-04.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Notifica relativa alla creazione risorsa ha esito positivo](images/AzureLabs-Lab3-05.png)
 
8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Verrà visualizzata per la nuova istanza del servizio LUIS. 
 
    ![L'accesso alle chiavi di LUIS](images/AzureLabs-Lab3-06.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio.
10. Dal *avvio rapido* pagina, delle *API LUIS* del servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** (è anche possibile ottenere questo risultato facendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave). Il servizio verrà visualizzata *chiavi*.
11. Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto. 
12. Nel *Service* pagina, fare clic su *portale di Language Understanding* essere reindirizzati alla pagina Web che verrà usato per creare il nuovo servizio, all'interno dell'App LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capitolo 2: il portale di Language Understanding

In questa sezione si apprenderà come creare un'App LUIS nel portale di LUIS. 

> [!IMPORTANT]
> Tenere presente, tale impostazione il *entità*, *Intent*, e *Utterances* all'interno di questo capitolo è solo il primo passaggio nella creazione del servizio LUIS: è necessario anche per Ripetere il training del servizio, più volte, quindi, per renderlo più accurate. Ripetizione del training del servizio viene trattato nel [ultimo capitolo](#chapter-12--improving-your-luis-service) di questo corso, pertanto è necessario verificare completarla.

1.  Al raggiungimento di *portale di Language Understanding*, potrebbe essere necessario eseguire l'accesso, se non si ha ancora, con le stesse credenziali come il portale di Azure. 

    ![Pagina di accesso di LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Se questa è la prima volta, Usa LUIS, è necessario scorrere verso il basso la parte inferiore della pagina di benvenuto, per trovare e fare clic sui **app LUIS creare** pulsante.

    ![Creare una pagina dell'app LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Una volta effettuato l'accesso, fare clic su **le mie app** (se non attualmente in quella sezione). È possibile fare clic su **Crea nuova app**.

    ![LUIS - l'immagine dell'App](images/AzureLabs-Lab3-09.png)
 
4.  Assegnare all'app un *nome*.
5.  Se l'app dovrebbe per comprendere una lingua diversa dall'inglese, è necessario modificare il *delle impostazioni cultura* per la lingua appropriata.
6.  Qui è anche possibile aggiungere un *descrizione* della nuova app LUIS.

    ![LUIS - creare una nuova app](images/AzureLabs-Lab3-10.png)

7.  Quando si preme **eseguite**, sarà necessario immettere il *compilare* pagina del nuovo *LUIS* dell'applicazione.
8.  Esistono alcuni concetti importanti di seguito:

    -   *Finalità*, rappresenta il metodo che verrà chiamato dopo una query da parte dell'utente. Un' *finalità* può avere uno o più *entità*.
    -   *Entity*, è un componente di query che descrive le informazioni rilevanti per il *INTENT*.
    -   *Espressioni*, vengono forniti esempi di query fornite dallo sviluppatore, userà tale LUIS per eseguire il training di se stesso.

Se questi concetti non sono perfettamente cancellare, comunque, questo corso chiarirà più avanti in questo capitolo.

Inizierà creando il *entità* necessari per compilare questo corso.

9.  Sul lato sinistro della pagina, fare clic su *Entities*, quindi fare clic su **Crea nuova entità**.

    ![Crea nuova entità](images/AzureLabs-Lab3-11.png)

10. Chiamare la nuova entità *colore*, impostarne il tipo *semplice*, quindi premere **eseguita**.

    ![Creare entità semplice - colore](images/AzureLabs-Lab3-12.png)
 
11. Ripetere questo processo di creazione di tre (3) più semplice entità denominate:

    -   *upsize*
    -   *downsize*
    -   *target*

Il risultato dovrebbe essere simile all'immagine seguente:

![Risultato della creazione di entità](images/AzureLabs-Lab3-13.png)
 
A questo punto è possibile iniziare a creare *Intent*. 

> [!WARNING]
> Non eliminare le **None** finalità.

12. Sul lato sinistro della pagina, fare clic su **Intent**, quindi fare clic su **Crea nuovo finalità**.

    ![Creare nuovo Intent](images/AzureLabs-Lab3-14.png)

13. Chiamare il nuovo *finalità* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Ciò *finalità* nome viene usato all'interno del codice più avanti in questo corso, pertanto, per ottenere risultati ottimali, usare questo nome esattamente come fornito.

Dopo aver verificato il nome che si verrà indirizzati alla pagina di Intent.

![LUIS - pagina Intent](images/AzureLabs-Lab3-15.png)

Si noterà che è presente una casella di testo che chiede al tipo 5 o più diverso *Utterances*.

> [!NOTE]
> LUIS converte tutte le espressioni in lettere minuscole.

14. Inserire il codice seguente *Utterance* nella casella di testo superiore (attualmente con il testo *digitare esempi circa 5...* ), quindi premere **invio**:

```
The color of the cylinder must be red
```

Si noterà che il nuovo *Utterance* verranno visualizzati in un elenco sotto.

In seguito lo stesso processo, inserire le seguenti espressioni sei (6):

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Per ogni Utterance che è stato creato, è necessario identificare le parole devono essere utilizzate dal servizio LUIS come entità. In questo esempio è necessario assegnare un'etichetta di tutti i colori come un *colore* entità e tutti i possibili riferimenti a una destinazione come una *destinazione* entità.

15. A tale scopo, provare a fare clic sulla parola *cilindro* nel primo Utterance e selezionare *destinazione*.

    ![Identificare le destinazioni Utterance](images/AzureLabs-Lab3-16.png)
 
16. Fare clic sulla parola *rossa* nel primo Utterance e selezionare *colore*.

    ![Identificare le entità Utterance](images/AzureLabs-Lab3-17.png)
 
17. Etichetta, inoltre, la riga successiva in cui *cubo* deve essere un *destinazione*, e *nero* deve essere un *colore*. Si noti inoltre l'utilizzo delle parole *'this'*, *','*, e *'questo oggetto'*, quale forniamo, quindi avere anche tipi di destinazione non specifiche disponibili. 

18. Ripetere il processo precedente fino a quando tutte le espressioni sono le entità denominate. Vedere la seguente immagine se ti serve assistenza.

    > [!TIP]
    > Quando si selezionano le parole per etichettarle come entità:
    > - Per singole parole fai clic su essi.
    > - Per un set di due o più parole, fare clic all'inizio e quindi alla fine del set.

    > [!NOTE]
    > È possibile usare la *Visualizza i token* pulsante Mostra/Nascondi per alternare **entità / token visualizzare**!

19. I risultati dovrebbero essere come illustrato nelle immagini seguenti, che mostra le **Entities / token visualizzare**:

    ![Viste di entità e i token](images/AzureLabs-Lab3-18.png)
  
20. A questo punto premere il **Train** pulsante in alto a destra della pagina e attendere che l'indicatore di arrotondamento piccolo in modo da diventare verde. Ciò indica che LUIS è stato correttamente eseguito il training riconosca questa finalità.

    ![Train LUIS](images/AzureLabs-Lab3-19.png)
 
21. Come esercizio per l'utente, creare una nuova con finalità di chiamata **ChangeObjectSize**, usando le entità *destinazione*, *upsize*, e *ridimensionare*.
22. Seguendo lo stesso processo come l'intento precedente, inserire le seguenti espressioni otto (8) per *dimensioni* modificare:

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

23. Il risultato dovrebbe essere simile a quello nell'immagine seguente:

    ![Configurare i token ChangeObjectSize / entità](images/AzureLabs-Lab3-20.png) 

24. Una volta, entrambe le finalità **ChangeObjectColor** e **ChangeObjectSize**, sono stati creati e sottoposti a training, fare clic sul **PUBLISH** pulsante nella parte superiore della pagina.

    ![Pubblicare il servizio LUIS](images/AzureLabs-Lab3-21.png)

25. Nel *pubblica* pagina verranno completate e pubblicare l'App LUIS in modo che sia accessibile dal codice.

    1. Impostare l'elenco verso il basso *Publish To* come **produzione**.
    2. Impostare il *Timezone* nel fuso orario locale.
    3. Selezionare la casella **Include tutti i prevista i punteggi di intent**.
    4. Fare clic su **pubblicare nello slot di produzione**.

        ![Impostazioni di pubblicazione](images/AzureLabs-Lab3-22.png)

26. Nella sezione *risorse e le chiavi*:

    1.  Selezionare l'area che è impostato per l'istanza di servizio nel portale di Azure.
    2.  Si noterà una **Starter_Key** elemento riportato di seguito, ignorarlo.
    3.  Fare clic su **Add Key** e inserire le *chiave* ottenuto nel portale di Azure quando si crea l'istanza del servizio. Se Azure e il portale di LUIS effettuati lo stesso utente, si riceveranno menu a discesa dei *nome del Tenant*, *il nome della sottoscrizione*e il *chiave* si desidera utilizzare ( avrà lo stesso nome come specificato in precedenza nel portale di Azure.

    > [!IMPORTANT] 
    > Trova di sotto *Endpoint*, eseguire una copia dell'endpoint corrispondente alla chiave sono stati inseriti, si verrà presto usarla nel codice.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capitolo 3-configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab3-24.png)

2.  A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR_LUIS**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Scegliere Modifica > Preferenze e dalla nuova finestra, quindi passare al **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab3-26.png)
 
4.  Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Passare a **File > Build Settings** e assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2. **Tipo di compilazione** è impostata su **D3D**
    3. **SDK** è impostata su **installata più recente**
    4. **Versione di Visual Studio** è impostata su **installata più recente**
    5. **Compilare ed eseguire** è impostata su **computer locale**
    6. Salvare la scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.
        
            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab3-28.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![Crea nuova cartella scripts](images/AzureLabs-Lab3-29.png)

        3. Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **MR_LuisScene**, quindi premere **Salva**.

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab3-30.png)

    7. Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

6. Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab3-31.png) 
 
7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1. **Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).
        2. **Back-end di scripting** deve essere **.NET**
        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab3-32.png)
      
    2. All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab3-33.png)

    3. Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab3-34.png)

8.  Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Impostazioni di compilazione.
10. Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).

## <a name="chapter-4--create-the-scene"></a>Capitolo 4: creazione della scena

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo nel progetto come un [pacchetto personalizzato ](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **piano**.

    ![Creare un piano.](images/AzureLabs-Lab3-35.png)

2.  Tenere presente che quando è fare doppio clic all'interno di *gerarchia* nuovamente per creare più oggetti, se hai ancora l'ultimo oggetto selezionato, l'oggetto selezionato sarà l'elemento padre del nuovo oggetto. Evitare di mouse in uno spazio vuoto all'interno della gerarchia e quindi facendo clic su.

3.  Ripetere questa procedura per aggiungere gli oggetti seguenti:

    1. *Sfera*
    2. *Cilindro*
    3. *Cubo*
    4. *Testo 3D*

4.  La scena risulta *gerarchia* dovrebbe essere simile a quello nell'immagine seguente:

    ![Impostazione di gerarchie di scena.](images/AzureLabs-Lab3-36.png)
 
5.  A sinistra fare clic sul **Main Camera** per selezionarlo, esaminare il *Pannello di controllo* verrà visualizzato l'oggetto della fotocamera con tutti i relativi componenti.
6.  Fare clic sui **Add Component** che si trova nella parte inferiore delle *Pannello di controllo*.

    ![Aggiungi origine Audio](images/AzureLabs-Lab3-37.png)
 
7.  Ricerca per il componente chiamato *origine Audio*, come illustrato in precedenza.
8.  Assicurarsi anche che il *trasformare* componente della fotocamera principale è impostato su (0, 0,0), questa operazione può essere eseguita facendo clic la **a forma di ingranaggio** icona accanto della Camera *trasformare* componente e selezionando **reimpostare**. Il *trasformare* componente sarà quindi simile:

    1.  *Posizione* è impostata su **0, 0, 0**.
    2.  *Rotazione* è impostata su **0, 0, 0**.

    > [!NOTE] 
    > Per il Microsoft HoloLens, sarà necessario modificare anche il comando seguente, che fanno parte del **fotocamera** componente, che è attivata il **Main Camera**:
    > - **Cancellare i flag:** Colore a tinta unita.
    > - **Sfondo** ' nero, Alpha 0'-colore esadecimale: #00000000.

9.  Fare clic sulla **piano** per selezionarlo. Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:

    |       | Trasformare - *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. Fare clic sulla **sfera** per selezionarlo. Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:

    |       | Trasformare - *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. Fare clic sulla **cilindro** per selezionarlo. Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:

    |       | Trasformare - *posizione* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. Fare clic sulla **cubo** per selezionarlo. Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:

    |        | Trasformare - *posizione* |       |  \| |       | Trasformare - *rotazione* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Fare clic sulla **nuovo testo** oggetto per selezionarlo. Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:

    |       | Trasformare - *posizione* |       |  \| |       | Trasformare - *scalabilità* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. Change **Font Size** nel **testo Mesh** componente **50**.
15. Modifica il *nome* delle **testo Mesh** oggetto **dettatura testo**.

    ![Creare l'oggetto testo 3D](images/AzureLabs-Lab3-38.png)
 
16. La struttura di gerarchia pannello sarà simile al seguente:

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab3-38b.png)


17. La scena finale dovrebbe essere simile all'immagine seguente:

    ![La visualizzazione di scena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capitolo 5: creare la classe MicrophoneManager

È il primo Script si intende creare il *MicrophoneManager* classe. In seguito, si creerà il *LuisManager*, il *comportamenti* (classe) e infine il *estasiati* (è possibile creare tutti questi ora, ma che verrà trattato come classe raggiungere ogni capitolo).

Il *MicrophoneManager* classe è responsabile per:

-   Rilevamento il dispositivo di registrazione associato a visore VR o machine (a seconda del valore è quello predefinito).
-   Acquisire l'audio (voce) e usare la dettatura per archiviarlo sotto forma di stringa.
-   Dopo la voce è stato sospeso, inviare la dettatura per il *LuisManager* classe. 

Per creare questa classe: 

1.  Fare doppio clic nella *Pannello di progetto*, **Crea > cartella**. Chiamare la cartella **script**. 

    ![Crea cartella Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Con il **script** cartella creata, fare doppio clic sopra per avviarlo. Quindi, all'interno di tale cartella, pulsante destro del mouse, **Crea > C# Script**. Denominare lo script *MicrophoneManager*. 

3.  Fare doppio clic su *MicrophoneManager* per aprirlo con *Visual Studio*.
4.  Aggiungere spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di *MicrophoneManager* classe:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto. Questi verranno chiamati quando inizializza la classe:

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
 
7.  A questo punto è necessario il metodo che l'App Usa per avviare e arrestare l'acquisizione voce e passarlo al *LuisManager* (classe), che verrà compilata a breve. 

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

8.  Aggiungere un *dettatura gestore* che verrà richiamato quando la voce viene sospesa. Questo metodo passerà il testo di dettatura dal *LuisManager* classe.

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
    > Eliminare il *Update ()* metodo poiché questa classe non verrà utilizzate.

9.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

    > [!NOTE]
    > A questo punto si noterà un errore dei *pannello della Console dell'Editor Unity*. Infatti, il codice fa riferimento il *LuisManager* classe che verrà creato nel capitolo successivo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capitolo 6: creare la classe LUISManager

È il momento in cui creare il *LuisManager* classe, che renderà la chiamata al servizio Azure LUIS. 

Lo scopo di questa classe è per ricevere il testo di dettatura dal *MicrophoneManager* classe e inviarle per il *API di Azure Language Understanding* da analizzare.

Eseguirà la deserializzazione di questa classe la *JSON* risposta e chiamare i metodi appropriati della *comportamenti* classe da attivare un'azione.

Per creare questa classe: 

1.  Fare doppio clic sui **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script *LuisManager*. 
3.  Fare doppio clic sullo script per aprirlo con Visual Studio.
4.  Aggiungere spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Inizierà creando tre classi **all'interno** il *LuisManager* classe (all'interno del file di script stesso, sopra la *Start ()* (metodo)) che rappresenterà il deserializzati Risposta JSON da Azure.

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

6.  Successivamente, aggiungere le variabili seguenti all'interno di *LuisManager* classe:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Assicurarsi di inserire l'endpoint di LUIS in ora (che sarà necessario dal portale di LUIS).

8.  Il codice per il *Awake()* metodo deve ora essere aggiunto. Questo metodo verrà chiamato quando si inizializza la classe:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  È ora necessario i metodi di questa applicazione usa per inviare la dettatura ricevuta dal *MicrophoneManager* classe *LUIS*, quindi ricevere e deserializzare la risposta. 
10. Dopo aver determinato il valore della finalità e le entità associate, vengono passati all'istanza del *comportamenti* classe per attivare l'azione desiderata.

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
 
11. Creare un nuovo metodo denominato *AnalyseResponseElements()* che leggerà risultante *AnalysedQuery* e determinare l'entità. Una volta vengono determinate le entità, verranno passate all'istanza del *comportamenti* classe da utilizzare nelle azioni.

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
    > Eliminare il *Start ()* e *Update ()* poiché questa classe non verrà utilizzati i metodi.

12. Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

> [!NOTE]
> A questo punto noterai che diversi errori dei *pannello della Console dell'Editor Unity*. Infatti, il codice fa riferimento il *comportamenti* classe che verrà creato nel capitolo successivo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capitolo 7: creare la classe di comportamenti

Il *comportamenti* classe attiverà le azioni con l'entità fornita dalle *LuisManager* classe.

Per creare questa classe: 

1.  Fare doppio clic sui **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script *comportamenti*. 
3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.
4.  Quindi aggiungere le variabili seguenti all'interno di *comportamenti* classe:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Aggiungere il *Awake()* codice del metodo. Questo metodo verrà chiamato quando si inizializza la classe:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  I seguenti metodi vengono chiamati i *LuisManager* classe (che è stato creato in precedenza) per determinare l'oggetto di destinazione della query e quindi attivare l'azione appropriata.

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
 
7.  Aggiungere il *FindTarget()* metodo per determinare quali le *Gameobject* è la destinazione delle finalità corrente. Questo metodo di impostazione predefinita è la destinazione per il *GameObject* in corso "gazed" Se non viene definita alcuna destinazione esplicite nelle entità.

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
    > Eliminare il *Start ()* e *Update ()* poiché questa classe non verrà utilizzati i metodi.

8.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capitolo 8: creare la classe sguardo

La classe ultimo che è necessario per completare questa app è il *estasiati* classe. Questa classe aggiorna il riferimento di *GameObject* attualmente in visivi dello stato attivo dell'utente.

Per creare questa classe: 

1.  Fare doppio clic sui **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script *estasiati*. 
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
 
5.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Capitolo 9: completamento dell'installazione di scena

1.  Per completare l'installazione della scena, trascinare ogni script che sono creati dalla cartella degli script per il **Main Camera** dell'oggetto nel *gerarchia pannello*.
2.  Selezionare il **Main Camera** ed esaminare le *Pannello di controllo*, dovrebbe essere possibile per ogni script che sono stati connessi e si noterà che esistono parametri che devono ancora essere impostato su ogni script.

    ![L'impostazione delle destinazioni di riferimento della fotocamera.](images/AzureLabs-Lab3-41.png)

3.  Per impostare questi parametri in modo corretto, seguire queste istruzioni:

    1. *MicrophoneManager*:

        - Dal *Pannello di gerarchia*, trascinare il **dettatura testo** nell'oggetto il **dettatura testo** casella di valore del parametro.

    2. *Comportamenti*, dal *gerarchia pannello*:

        - Trascinare il **sfera** all'oggetto il *sfera* la destinazione di riferimento.
        - Trascinare il **cilindro** nel *cilindro* la destinazione di riferimento.
        - Trascinare il **cubo** nel *cubo* la destinazione di riferimento.

    3. *Estasiati*:

        - Impostare il *estasiati distanza massima* al **300** (se non è già). 

4.  Il risultato dovrebbe essere simile all'immagine seguente:

    ![Ora che mostra le destinazioni di riferimento della fotocamera, impostare.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capitolo 10: Test nell'Editor di Unity

Verificare che il programma di installazione di scena sia implementato correttamente.

Verifica che:

-   Tutti gli script associati per il **Main Camera** oggetto. 
-   Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.

1.  Premere il **riprodurre** pulsante il *Editor di Unity*. L'App dovrebbe essere eseguito all'interno di visore VR immersivi collegati.

2.  Provare alcune espressioni, ad esempio:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Se viene visualizzato un errore nella console di Unity sul dispositivo audio predefinito modifica, la scena potrebbe non funzionare come previsto. Ciò è dovuto al modo in cui che il portale di realtà mista si occupa microfoni incorporati per auricolari sia disponibile. Se è visualizzato questo errore, è sufficiente arrestare la scena e avviarla nuovamente e cose dovrebbero funzionare come previsto.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capitolo 11: compilazione e trasferire localmente la soluzione di piattaforma UWP

Dopo aver verificato che l'applicazione funziona nell'Editor di Unity, si è pronti per compilare e distribuire.

Per compilare:

1.  Salvare nella scena corrente facendo clic su **File > Salva**.
2.  Passare a **File > Impostazioni di compilazione**.
3.  Selezionare la casella denominata **Unity C# progetti** (utile per la visualizzazione e debug del codice dopo aver creato il progetto UWP.
4.  Fare clic su **aggiungere scene Open**, quindi fare clic su **compilazione**.

    ![Finestra delle impostazioni di compilazione](images/AzureLabs-Lab3-43.png)

4.  Viene chiesto di selezionare la cartella in cui si desidera compilare la soluzione. 

5.  Creare un *COMPILAZIONI* cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta. 
6.  Fare clic su **selezionare la cartella** per avviare la compilazione nel percorso specificato.
 
    ![Crea cartella Compilazioni](images/AzureLabs-Lab3-44.png)
    ![selezionare Crea cartella](images/AzureLabs-Lab3-45.png)
 
7.  Una volta Unity ha terminato (potrebbe richiedere alcuni minuti) predefiniti, dovrebbe aprirsi una **Esplora File** finestra in corrispondenza della posizione della compilazione.

Per distribuire nel computer locale:

1.  Nelle *Visual Studio*, aprire il file di soluzione che è stato creato nel [capitolo precedente](#chapter-10--test-in-the-unity-editor).
2.  Nel **piattaforma soluzione**, selezionare **x86**, **macchina locale**.
3.  Nel **configurazione della soluzione** selezionate **Debug**.

    > Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso. Tuttavia, è necessario inoltre eseguire le operazioni seguenti:
    > - Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare. 
    > - Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.

    ![Distribuire App](images/AzureLabs-Lab3-46.png)
 
4.  Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.
5.  L'App deve vengono ora visualizzati nell'elenco delle App installate, pronta per essere avviata.
6.  Una volta avviata, l'App verrà richiesto di autorizzare l'accesso per il _microfono_. Usare il *controller di movimento*, o *Input vocale*, o il *tastiera* necessario premere il **Sì** pulsante. 

## <a name="chapter-12--improving-your-luis-service"></a>Capitolo 12: migliorare il servizio LUIS

>[!IMPORTANT] 
> In questo capitolo è molto importante e potrebbe essere necessario scorrere su più volte, evitare di migliorare l'accuratezza del servizio LUIS: verificare di aver completato questa.

Per migliorare il livello di informazioni fornite da LUIS è necessario acquisire nuove espressioni e usarli per ripetere il training dell'App LUIS.

Ad esempio, si potrebbe aver eseguito il training LUIS per comprendere "Increase" e "Ci", ma non si vuole che l'app anche per comprendere parole come "Ingrandisci"?

Dopo aver usato l'applicazione più volte, tutto ciò che avrebbe dovuto dirlo verranno raccolti dal servizio LUIS e disponibili nel portale di LUIS.

1.  Passare all'applicazione del portale seguendo questa [collegamento](https://www.luis.ai/home)e nel Log.
2.  Una volta che si è connessi con le Credentials MS, fare clic sui *nome App*.
3.  Scegliere il **esaminare utterances endpoint** pulsante a sinistra della pagina.

    ![Espressioni di revisione](images/AzureLabs-Lab3-47.png)
 
4.  Si verrà visualizzato un elenco di espressioni che sono state inviate al servizio LUIS per le applicazioni di realtà mista.

    ![Elenco di espressioni](images/AzureLabs-Lab3-48.png)
 
Noteranno alcune evidenziato *Entities*. 

Passando il puntatore del mouse su ogni parola evidenziata, è possibile esaminare ogni Utterance e determinare quali entità è stato riconosciuto correttamente, quali entità sono errate e quali non sono presenti entità.

Nell'esempio precedente, è emerso che era stata evidenziata la parola "spear" come destinazione, pertanto è necessario correggere l'errore, questa operazione viene eseguita al passaggio del mouse sulla parola con il mouse e scegliendo **Rimuovi etichetta**.

![Controllare utterances](images/AzureLabs-Lab3-49.png)
![Rimuovi etichetta immagine](images/AzureLabs-Lab3-50.png)
 
5.  Se si ritiene di espressioni che non sono completamente errate, è possibile eliminarli usando il **eliminare** pulsante sul lato destro dello schermo.

    ![Elimina utterances errato](images/AzureLabs-Lab3-51.png)

6.  O se si ritiene che LUIS ha interpretato il Utterance correttamente, è possibile convalidare la comprensione utilizzando il **Aggiungi a allineato con finalità di** pulsante.

    ![Aggiungere finalità allineato](images/AzureLabs-Lab3-52.png)

7.  Dopo aver ordinato tutte le espressioni visualizzate, provare e ricaricare la pagina per verificare se informazioni sono disponibili.
8.  È molto importante ripetere questo processo le volte che è possibile migliorare la comprensione dell'applicazione. 

**Buon divertimento!**

## <a name="your-finished-luis-integrated-application"></a>L'applicazione LUIS integrata completata

Complimenti, è stata compilata un'app per realtà mista che sfrutta Azure Language Understanding Intelligence Service, per comprendere ciò che viene visualizzato un utente e agire su tali informazioni.

![risultato di Lab](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Quando si usa questa applicazione è possibile notare che se si fissare oggetto Floor e richiedere di modificare il colore, verranno eseguite in modo. È possibile usare le modalità arrestare l'applicazione di modificare il colore della base?

### <a name="exercise-2"></a>Esercizio 2

Provare a estendere le funzionalità di LUIS e App, aggiunta di funzionalità aggiuntive per gli oggetti nella scena; ad esempio, creare nuovi oggetti alla sguardo punto hit, a seconda di ciò che l'utente indicato e quindi essere in grado di utilizzare tali oggetti insieme a oggetti di scena corrente, con i comandi esistenti. 
