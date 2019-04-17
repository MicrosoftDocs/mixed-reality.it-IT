---
title: MR e Azure 301 - traduzione
description: Completare questo corso di informazioni su come implementare l'API traduzione testuale Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, traduzione testuale Microsoft translator, hololens, coinvolgenti, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603611"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR e Azure 301: Traduzioni

In questo corso, si apprenderà come aggiungere funzionalità di conversione a un'applicazione di realtà mista tramite servizi cognitivi di Azure, con l'API traduzione testuale.

![Versione finale del prodotto](images/AzureLabs-Lab1-00.png)

L'API traduzione testuale è una servizio che funziona quasi in tempo reale di conversione. Il servizio è basato sul cloud e, tramite una chiamata API REST, possa rendere un'app per usare la tecnologia di traduzione automatica neurale per tradurre il testo in un altro linguaggio. Per altre informazioni, visitare il [pagina API traduzione testuale Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  L'utente leggerà in un microfono connessi a un auricolare (VR) coinvolgenti (o il microfono incorporato di HoloLens).
2.  L'app verrà acquisire la dettatura e inviarlo per l'API traduzione testuale di Azure.
3.  Il risultato di traduzione verrà visualizzato in un gruppo dell'interfaccia utente semplice nella scena Unity.

Questo corso ti spiegherà come ottenere i risultati dal servizio di Microsoft Translator in un'applicazione di esempio basate su Unity. Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 301: Traduzioni</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Le cuffie con un microfono incorporato (se le cuffie non è presente un mic incorporati e altri relatori)
- Accesso a Internet per il recupero di programma di installazione e la conversione di Azure

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
- Il codice in questa esercitazione è possibile registrare dal dispositivo microfono predefinito connesso al PC. Assicurarsi che il dispositivo di microfono predefinito viene impostato per il dispositivo che si intende usare per acquisire la voce dell'utente.
- Per consentire al computer abilitare la dettatura, passare a **Impostazioni > Privacy > vocale, input penna e digitando** e selezionare il pulsante **Turn On servizi di riconoscimento vocale e i suggerimenti di digitazione**.
- Se si usa un microfono e cuffie connesso a (o incorporato in) le cuffie, assicurarsi che l'opzione "Quando wear my le cuffie, passare a microfono auricolare" attivata nel **Impostazioni > realtà mista > Audio e vocale**.

   ![Impostazioni di realtà mista](images/AzureLabs-Lab1-00-5.png)

   ![Impostazione di microfono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Tenere presente che se si sta sviluppando per un visore VR immersivi per questo lab, potrebbero verificarsi problemi di dispositivo di output audio. Si è verificato un errore con Unity, che è stato risolto in versioni successive di Unity (Unity 2018.2). Il problema impedisce Unity di cambiare il dispositivo di output audio predefinito in fase di esecuzione. Come per risolvere il problema, assicurarsi di che aver completato i passaggi precedenti, chiudere e riaprire l'Editor, quando questo problema si manifesta.

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: il portale di Azure

Per usare l'API di traduzione di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.

1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** in alto a sinistra angolo e cercare "API traduzione testuale." Selezionare **immettere**.

    ![Nuova risorsa](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  La nuova pagina fornirà una descrizione del *API traduzione testuale* servizio. AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![Crea servizio API di traduzione testo](images/AzureLabs-Lab1-03.png)

4.  Dopo avere fatto clic su **Create**:

    1. Inserire la posizione desiderata **nome** per questa istanza del servizio.
    2. Selezionare un'opzione appropriata **sottoscrizione**.
    3. Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *servizio di traduzione testo*, un livello gratuito, denominato F0, debba essere disponibile.
    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    6. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.
    7. Selezionare **Create**.

        ![Selezionare il pulsante Crea.](images/AzureLabs-Lab1-04.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.
6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale. 

    ![Notifica di creazione del servizio Azure](images/AzureLabs-Lab1-05.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Passare alla finestra popup di risorse.](images/AzureLabs-Lab1-06.png)

8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati all'istanza del servizio API di traduzione testo nuovo. 

    ![Pagina del servizio API di testo Microsoft Translator](images/AzureLabs-Lab1-07.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio. 
10. Dal *avvio rapido* pagina delle *traduzione testuale Microsoft Translator* servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** (è possibile anche ottenere questo risultato facendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave). Il servizio verrà visualizzata *chiavi*.
11. Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Configurare e testare il visore VR immersivi di realtà mista.

> [!NOTE]
> A questo corso non è necessario il controller di movimento. Se è necessario il supporto di configurazione di un visore VR immersivi, please [seguire questa procedura](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

Di seguito è un set tipico backup per lo sviluppo con realtà mista e, di conseguenza, è un buon modello per altri progetti:

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab1-08.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **MR_Translation**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab1-10.png)

4.  Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab1-11.png)

5.  Passare a **File > Build Settings** e assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2. **Tipo di compilazione** è impostata su **D3D**
    3. **SDK** è impostata su **installata più recente**
    4. **Versione di Visual Studio** è impostata su **installata più recente**
    5. **Compilare ed eseguire** è impostata su **computer locale**
    6. Salvare la scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab1-12.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![Crea nuova cartella scripts](images/AzureLabs-Lab1-13.png)

        3. Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **MR_TranslationScene**, quindi premere **Salva**.

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab1-14.png)

            > Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity. Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.

    7. Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

6. Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab1-15.png)

7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1. **Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).
        2. **Back-end di scripting** deve essere **.NET**
        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab1-16.png)
      
    2. All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab1-17.png)

    3. Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab1-18.png)

8.  Nuovamente in **Build Settings**, *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Impostazioni di compilazione.
10. Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3: impostazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo nel progetto come un [ *Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-results-class). È comunque necessario creare un progetto Unity.

1.  Nel *Pannello di gerarchia*, si noterà un oggetto denominato **Main Camera**, questo oggetto rappresenta il punto di vista della "head" quando si è "l'applicazione interni".
2.  Con il Dashboard di Unity fronte, selezionare la **Main Camera GameObject**. Si noterà che il *Pannello di controllo* (in genere trovato a destra, all'interno del Dashboard) mostrerà i vari componenti di tale *GameObject*, con *trasformare* nella parte superiore, seguita da *fotocamera*e alcuni altri componenti. È necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionato correttamente.
3.  A questo scopo, selezionare la **a forma di ingranaggio** icona accanto della fotocamera *trasformare* componente e selezionando **Reimposta**. 

    ![Reimpostare la trasformazione Main Camera.](images/AzureLabs-Lab1-19.png)
 
4.  Il *trasformare* componente sarà quindi simile:

    1. Il *posizione* è impostata su **0, 0, 0**
    2. *Rotazione* è impostata su **0, 0, 0**
    3. E *scalabilità* è impostata su **1, 1, 1**

        ![Trasformare le informazioni per la fotocamera](images/AzureLabs-Lab1-20.png)

5.  Successivamente, con la **Main Camera** oggetti selezionati, vedere il **Add Component** che si trova nella parte inferiore del *Pannello di controllo*. 
6.  Selezionare questo pulsante e di ricerca (digitandone *origine Audio* nel campo di ricerca o passare le sezioni) per il componente denominato **origine Audio** come illustrato di seguito e selezionarlo (premendo INVIO su di esso funziona anche).
7.  Un' *origine Audio* verrà aggiunto al componente la **Main Camera**, come illustrato di seguito.

    ![Aggiungere un componente di origine Audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Per Microsoft HoloLens, sarà necessario modificare anche il comando seguente, che fanno parte del **fotocamera** componente le **Main Camera**:
    > - **Cancellare i flag:** Colore a tinta unita.
    > - **Sfondo** ' nero, Alpha 0'-colore esadecimale: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capitolo 4: configurazione Debug Canvas

Per visualizzare l'input e output della conversione, è necessario creare un'interfaccia utente di base. A questo corso, si creerà un oggetto di interfaccia utente di Canvas con vari oggetti 'Text' per visualizzare i dati.

1.  Pulsante destro del mouse in un'area vuota della *pannello gerarchia*, in **UI**, aggiungere un **Canvas**.

    ![Aggiungere nuovo oggetto area di disegno dell'interfaccia utente.](images/AzureLabs-Lab1-22.png)

2.  Con l'oggetto Canvas selezionato, nella *Pannello di controllo* (all'interno del componente 'Area di disegno'), cambiare **modalità di rendering** a **spazio globale**. 
3.  Successivamente, modificare i parametri seguenti nel *Rect trasformazione del Pannello di controllo*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Larghezza* : 500
    3. *Altezza* - 300
    4. *Scala* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Aggiornare la trasformazione rect per l'area di disegno.](images/AzureLabs-Lab1-23.png)
 
4.  Fare clic con il pulsante destro sul **Canvas** nel *pannello gerarchia*, sotto **dell'interfaccia utente**e aggiungere un **pannello**. Ciò **pannello** fornirà uno sfondo per il testo che si prevede di visualizzare nella scena.
5.  Fare clic con il pulsante destro sul **pannello** nel *pannello gerarchia*, sotto **dell'interfaccia utente**e aggiungere un **oggetto testo**. Ripetere lo stesso processo finché vengono creati quattro oggetti di testo dell'interfaccia utente in totale (Suggerimento: se hai selezionato il primo oggetto di 'Testo', è possibile premere semplicemente **'Ctrl' + era '**, in caso di necessità, fino a quando non si avranno quattro in totale). 
6.  Per ogni **oggetto testo**, selezionarlo e usare le seguenti tabelle per impostare i parametri *Pannello di controllo*.

    1. Per il *Rect trasformazione* componente:

        | Nome                   | Trasformare - *posizione*             | Larghezza      | Altezza    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Per il **testo (Script)** componente:


        | Nome                   | Testo               | Dimensione carattere    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Stato microfono: | 20           |
        | AzureResponseLabel     | Risposta Web di Azure | 20           |
        | DictationLabel         |   Hai appena detto:   | 20           |
        | TranslationResultLabel |    Conversione:    | 20           |

        ![Immettere i valori corrispondenti per le etichette dell'interfaccia utente.](images/AzureLabs-Lab1-24.png)

    3. Assicurarsi, inoltre, lo stile del carattere **grassetto**. Il testo in questo modo più semplice da leggere.

        ![Tipo di carattere grassetto.](images/AzureLabs-Lab1-25.png)

7.  Per ognuno *oggetto testo dell'interfaccia utente* creato nel [capitolo 5](#chapter-5--create-the-results-class), creare un nuovo *figlio* **oggetto testo dell'interfaccia utente**. Questi elementi figlio verranno visualizzato l'output dell'applicazione. Creare *figlio* oggetti tramite il pulsante destro del tuo genitore desiderato (ad esempio *MicrophoneStatusLabel*) e quindi selezionare **UI** e quindi selezionare **testo**.
8.  Per ognuno di questi elementi figlio, selezionarlo e usare le tabelle per impostare i parametri nel Pannello di controllo seguenti.

    1. Per il **Rect trasformazione** componente:

        | Nome                  | Trasformare - *posizione* | Larghezza      | Altezza    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X Z Y -30 0 0          | 300        | 30        |
        | AzureResponseText     | X Z Y -30 0 0          | 300        | 30        |
        | DictationText         | X Z Y -30 0 0          | 300        | 30        |
        | TranslationResultText | X Z Y -30 0 0          | 300        | 30        |

    2. Per il **testo (Script)** componente:

        | Nome                  | Testo          | Dimensione carattere    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Successivamente, selezionare l'opzione di allineamento 'centre' per ogni componente di testo:

    ![Allinea il testo.](images/AzureLabs-Lab1-26.png)

10. Per garantire la **testo dell'interfaccia utente figlio** gli oggetti sono facilmente leggibili, modificare le *colore*. Eseguire questa operazione, fare clic sulla barra dei (attualmente ' nero') accanto a *colore*. 

    ![Immettere i valori per gli output di testo dell'interfaccia utente corrispondente.](images/AzureLabs-Lab1-27.png)
 
11. Quindi, nella nuova, piccola, *colore* finestra Modifica il *colore esadecimale* per: **0032EAFF**

    ![Aggiornare il colore blu.](images/AzureLabs-Lab1-28.png)
 
12. Di seguito è riportato il **dell'interfaccia utente** dovrebbe avere un aspetto.
    1.  Nel *gerarchia pannello*:

        ![La gerarchia è la struttura fornita.](images/AzureLabs-Lab1-29.png)

    2.  Nel *scena* e *visualizzazioni di giochi*:

        ![Disporre le visualizzazioni scena e giochi nella stessa struttura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capitolo 5: creare la classe di risultati

È il primo script è necessario creare il *risultati* (classe), che è responsabile di fornire un modo per visualizzare i risultati della conversione. La classe archivia e visualizza quanto segue: 

- Il risultato della risposta da Azure.
- Lo stato di microfono. 
- Il risultato della dettatura (sintesi vocale).
- Il risultato della traduzione.

Per creare questa classe: 

1.  Fare doppio clic nella *Pannello di progetto*, quindi **Crea > cartella**. Denominare la cartella **script**. 
 
    ![Crea cartella scripts.](images/AzureLabs-Lab1-31.png)

    ![Aprire la cartella degli script.](images/AzureLabs-Lab1-32.png)
 
2.  Con il **script** cartella creare, fare doppio clic sopra per avviarlo. Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea >** quindi  **C# Script**. Denominare lo script *risultati*. 

    ![Creare il primo script.](images/AzureLabs-Lab1-33.png)
 
3.  Fare doppio clic su nuova *risultati* script per aprirlo con **Visual Studio**.
4.  Inserisci gli spazi dei nomi seguenti:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Quindi aggiungere il *Awake()* metodo, che verrà chiamato quando si inizializza la classe. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Infine, aggiungere i metodi che sono responsabili per l'output di varie informazioni relative ai risultati all'interfaccia utente. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capitolo 6: creare il *MicrophoneManager* classe

Si intende creare la seconda classe è il *MicrophoneManager*.

Questa classe è responsabile per:

- Rilevamento il dispositivo di registrazione associato a visore VR o machine (a seconda del valore è il valore predefinito).
- Acquisire l'audio (voce) e usare la dettatura per archiviarlo sotto forma di stringa.
- Dopo la voce è stato sospeso, inviare la dettatura alla classe del convertitore.
- Ospitare un metodo che può arrestare l'acquisizione voce se lo si desidera.

Per creare questa classe: 
1.  Fare doppio clic sui **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script *MicrophoneManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il *MicrophoneManager* classe:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Quindi, aggiungere le variabili seguenti all'interno di *MicrophoneManager* classe:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto. Questi verranno chiamati quando inizializza la classe:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  È possibile *eliminare* le *Update ()* metodo poiché questa classe non verrà utilizzate.
8.  È ora necessario i metodi usati dall'App per avviare e arrestare l'acquisizione voce e passarlo al *traduttore* (classe), che verrà compilata a breve. Copiare il codice seguente e incollarlo sotto la *Start ()* (metodo).

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Anche se questa applicazione non apporterà di usarla, il *StopCapturingAudio()* metodo è stato incluso anche in questo caso, se si vuole implementare la possibilità di arrestare l'acquisizione audio nell'applicazione.

9.  È ora necessario aggiungere un gestore di dettatura che verrà richiamato quando si arresta la voce. Questo metodo passa il testo dettato per il *traduttore* classe.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.

> [!WARNING]  
> A questo punto si noterà un errore dei *Console di Editor di Unity* pannello ("il nome 'Conversione' non esiste..."). Infatti, il codice fa riferimento il *traduttore* (classe), che verrà creato nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capitolo 7 su chiamata al servizio di Azure e Microsoft translator

È l'ultimo script è necessario creare il *traduttore* classe. 

Questa classe è responsabile per:

-   L'autenticazione all'App con *Azure*, in exchange per un' **Token di autenticazione**.
-   Usare il **Auth Token** per inviare testo (ricevuto dal *MicrophoneManager* classe) da tradurre.
-   Ricevere il risultato convertito e passarlo al *risultati* classe da visualizzare nell'interfaccia utente.

Per creare questa classe: 
1.  Andare alla **script** cartella creata in precedenza. 
2.  Fare doppio clic nella **Pannello di progetto**, **Crea > C# Script**. Chiamare lo script *traduttore*.
3.  Fare doppio clic su nuova *traduttore* script per aprirlo **con Visual Studio**.
4.  Aggiungere spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di *traduttore* classe:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Le lingue inserite i linguaggi **enum** sono solo esempi. È possibile aggiungere più se si vuole; il [API supporta oltre 60 lingue](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (inclusi Klingon).
    > - È presente una [pagina più interattiva copertura delle lingue disponibili](https://www.microsoft.com/translator/business/languages/), tenere tuttavia presente la pagina viene visualizzata solo quando la lingua del sito è impostata su "en-us' (e il sito di Microsoft verranno probabilmente di reindirizzamento per la sua lingua madre). È possibile modificare la lingua nella parte inferiore della pagina o modificando l'URL del sito.
    > - Il **authorizationKey** valore, nel frammento di codice precedente, deve essere il **chiave** ricevuto la sottoscrizione per il *API traduzione testuale di Azure*. Questa attività è stata descritta nella [capitolo 1](#chapter-1--the-azure-portal).

6.  Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto. 
7.  In questo caso, il codice effettua una chiamata a *Azure* usando la chiave di autorizzazione per ottenere un *Token*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Il token scade dopo 10 minuti. A seconda dello scenario per l'app, potrebbe essere necessario apportare la stessa coroutine chiamare più volte.

8.  Le coroutine per ottenere il Token è il seguente:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Se si modifica il nome del metodo IEnumerator **GetTokenCoroutine()**, è necessario aggiornare il *StartCoroutine* e *StopCoroutine* chiamare i valori stringa nel codice precedente. [In base alla documentazione di Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), per arrestare uno specifico *Coroutine*, è necessario usare il metodo di valore di stringa.

9.  Successivamente, aggiungere le coroutine (con un metodo flusso "supporto" immediatamente di sotto) per ottenere la traduzione del testo ricevuto dal *MicrophoneManager* classe. Questo codice crea una stringa di query da inviare per la *API traduzione testuale Azure*e quindi Usa la classe di Unity UnityWebRequest interna per effettuare una chiamata a 'Get' per l'endpoint con la stringa di query. Il risultato viene quindi utilizzato per la conversione del set nell'oggetto risultati. Il codice seguente illustra l'implementazione:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Capitolo 8: configurare la scena Unity

1.  Indietro nell'Editor di Unity, fare clic e trascinare il *risultati* classe *dalla* il **script** cartella in cui la **Main Camera** oggetto nel  *Pannello gerarchia*.
2.  Fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*. Si noterà che all'interno di appena aggiunta *Script* componente, sono presenti quattro campi con valori vuoti. Questi sono i riferimenti all'output per le proprietà nel codice. 
3.  Trascinare l'appropriato **testo** oggetti dal *gerarchia pannello* a questi quattro slot, come illustrato nell'immagine seguente.

    ![Aggiornare i riferimenti di destinazione con valori specificati.](images/AzureLabs-Lab1-34.png)
  
4.  Successivamente, fare clic e trascinare il *Translator* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*. 
5.  Quindi fare clic e trascinare il *MicrophoneManager* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*. 
6.  Infine, fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*. Si noterà che nello script che è stato trascinato sul, esistono due caselle che ti permetterà di impostare le lingue a discesa.
 
    ![Verificare che le lingue di traduzione previsto costituiscono l'input.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capitolo 9: Test nella realtà mista

A questo punto è necessario verificare che la scena sia stata implementata correttamente.

Verifica che:

- Tutte le impostazioni indicate nella [capitolo 1](#chapter-1--the-azure-portal) siano impostate correttamente. 
- Il *risultati*, *Translator*, e *MicrophoneManager*, gli script sono associati ai **Main Camera** oggetto. 
- È stato inserito il *API traduzione testuale di Azure* Service **chiave** all'interno del **authorizationKey** variabile all'interno del *Translator* copione.  
- Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.
- Il microfono funzioni durante l'esecuzione della scena (in caso contrario, verificare che il microfono associato sia la *predefiniti* dispositivo e aver [configurarlo correttamente all'interno di Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

È possibile testare il visore VR immersivi premendo la **riprodurre** pulsante il *Editor di Unity*.
L'App dovrebbe funzionare attraverso il visore VR immersivi collegati.

> [!WARNING]  
> Se viene visualizzato un errore nella console di Unity sul dispositivo audio predefinito modifica, la scena potrebbe non funzionare come previsto. Ciò è dovuto al modo in cui che il portale di realtà mista si occupa microfoni incorporati per auricolari sia disponibile. Se è visualizzato questo errore, è sufficiente arrestare la scena e avviarla nuovamente e cose dovrebbero funzionare come previsto.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capitolo 10: creare la soluzione di piattaforma UWP e trasferirla in locale nel computer locale

Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a **impostazioni di compilazione**: **File > Impostazioni di compilazione...**
2.  Dal **Build Settings** finestra, fare clic su **compilazione**.

    ![Compilare la scena Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Se non è già, graduazione **Unity C# progetti**.
4.  Fai clic su **Compila**. Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo *App*. Quindi con il *App* cartella selezionata, premere **Seleziona cartella**. 
5.  Unity verrà avviata la compilazione del progetto per la *App* cartella. 
6.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-11--deploy-your-application"></a>Capitolo 11: distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova build Unity (le *App* cartella) e aprire il file di soluzione con *Visual Studio*.
2.  Selezione configurazione di soluzione **Debug**.
3.  La piattaforma della soluzione, selezionare **x86**, **computer locale**. 

    > Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso. Tuttavia, è necessario inoltre eseguire le operazioni seguenti:
    > - Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare. 
    > - Assicurarsi *modalità sviluppatore* viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione al computer.
5.  L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.
6.  Una volta avviata, l'App verrà richiesto di autorizzare l'accesso al microfono. Assicurarsi di selezionare il **Sì** pulsante.
7.  È ora pronti per iniziare a tradurre.

## <a name="your-finished-translation-text-api-application"></a>L'applicazione API traduzione testuale conversione completata

Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API di testo Azure traduzioni per convertire testo parlato in testo tradotto.

![Prodotto finale.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

È possibile aggiungere funzionalità di sintesi vocale per l'app, in modo che il testo restituito viene pronunciato?

### <a name="exercise-2"></a>Esercizio 2

Consentono all'utente di modificare le lingue di origine e di output ('from' e 'a') all'interno dell'app stessa, in modo che l'app non dovrà essere ricompilato ogni volta che si desidera modificare le lingue.
