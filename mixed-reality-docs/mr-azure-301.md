---
title: MR e Azure 301-traduzione in lingua
description: Completare questo corso per apprendere come implementare il API Traduzione testuale di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, traduzione testuale, hololens, immersiva, VR
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554018"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR e Azure 301: Traduzioni

In questo corso si apprenderà come aggiungere funzionalità di traduzione a un'applicazione di realtà mista usando servizi cognitivi di Azure, con il API Traduzione testuale.

![Prodotto finale](images/AzureLabs-Lab1-00.png)

Il API Traduzione testuale è un servizio di traduzione che funziona quasi in tempo reale. Il servizio è basato sul cloud e, usando una chiamata API REST, un'app può usare la tecnologia di traduzione dei computer neurali per tradurre il testo in un'altra lingua. Per ulteriori informazioni, visitare la [pagina API traduzione testuale di Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  L'utente parlerà di un microfono connesso a un headset immersivo (VR) o del microfono incorporato di HoloLens.
2.  L'app acquisisce la dettatura e la invia al API Traduzione testuale di Azure.
3.  Il risultato della conversione verrà visualizzato in un gruppo di interfaccia utente semplice nella scena Unity.

Questo corso spiegherà come ottenere i risultati dal servizio di conversione in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 301: Traduzioni</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)
- Accesso a Internet per l'installazione e il recupero della traduzione in Azure

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
- Il codice in questa esercitazione consentirà di registrare dal dispositivo microfono predefinito connesso al PC. Verificare che il dispositivo microfonico predefinito sia impostato sul dispositivo che si intende usare per acquisire la voce.
- Per consentire al PC di abilitare la dettatura, passare a **impostazioni > Privacy > vocale, Inking &** digitando e selezionare il pulsante **Attiva servizi vocali e digitando suggerimenti**.
- Se si usa un microfono e cuffie connesse a (o incorporata), assicurarsi che l'opzione "quando si indossa la cuffia, passa alla cuffia auricolare" sia attivata in **impostazioni > realtà mista > audio e sintesi vocale**.

   ![Impostazioni della realtà mista](images/AzureLabs-Lab1-00-5.png)

   ![Impostazione del microfono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Si tenga presente che, se si sta sviluppando per un auricolare immersivo per questo Lab, è possibile che si verifichino problemi di dispositivo di output audio. Ciò è dovuto a un problema di Unity, che è stato risolto nelle versioni successive di Unity (Unity 2018,2). Il problema impedisce a Unity di modificare il dispositivo di output audio predefinito in fase di esecuzione. Per risolvere il problema, assicurarsi di aver completato i passaggi precedenti, quindi chiudere e riaprire l'editor quando si presenta questo problema.

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: portale di Azure

Per usare l'API di Azure translator, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.

1.  Accedere al portale di [Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare "API traduzione testuale". Premere **invio**.

    ![Nuova risorsa](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  La nuova pagina fornirà una descrizione del servizio *API traduzione testuale* . Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![Crea servizio API Traduzione testuale](images/AzureLabs-Lab1-03.png)

4.  Una volta fatto clic su **Crea**:

    1. Inserire il **nome** desiderato per l'istanza del servizio.
    2. Selezionare una **sottoscrizione**appropriata.
    3. Selezionare il  piano tariffario appropriato. se è la prima volta che si crea un *servizio di traduzione testuale*, è necessario che sia disponibile un livello gratuito (denominato F0).
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    6. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.
    7. Selezionare **Create**.

        ![Fare clic sul pulsante Crea.](images/AzureLabs-Lab1-04.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.
6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale. 

    ![Notifica di creazione del servizio di Azure](images/AzureLabs-Lab1-05.png)

7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Passare a finestra popup risorsa.](images/AzureLabs-Lab1-06.png)

8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio API Traduzione testuale. 

    ![Pagina servizio API Traduzione testuale](images/AzureLabs-Lab1-07.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio. 
10. Dalla pagina *avvio rapido* del servizio *traduzione testuale* passare al primo passaggio, recuperare *le chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti di collegamento ipertestuale blu disponibili nel menu di navigazione servizi, indicato dall'icona della chiave). Le *chiavi*del servizio vengono rivelate.
11. Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Configurare e testare l'auricolare immersiva della realtà mista.

> [!NOTE]
> Non sarà necessario alcun controller di movimento per questo corso. Se è necessario supporto per la configurazione di un auricolare immersivo, [attenersi alla seguente procedura](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, è un modello valido per altri progetti:

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab1-08.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **MR_Translation**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab1-10.png)

4.  Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab1-11.png)

5.  Passare a **File > impostazioni di compilazione** e verificare che:

    1. Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2. Il **tipo di compilazione** è impostato su **D3D**
    3. **SDK** è impostato sull' **ultima versione installata**
    4. La **versione di Visual Studio** è impostata su **installazione più recente**
    5. **Compilazione ed esecuzione** è impostato su **computer locale**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab1-12.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![Crea nuova cartella script](images/AzureLabs-Lab1-13.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_TranslationScene**e quindi fare clic su **Salva**.

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab1-14.png)

            > Tenere presente che è necessario salvare le scene Unity all'  interno della cartella assets, in quanto devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7. Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

6. Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab1-15.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1. La **versione di runtime** di scripting deve essere **stabile** (equivalente a .NET 3,5).
        2. Il **back-end** di scripting deve essere **.NET**
        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab1-16.png)
      
    2. Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        1. **InternetClient**
        2. **Microfono**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab1-17.png)

    3. Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab1-18.png)

8.  Nelle **impostazioni di compilazione**, *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra impostazioni di compilazione.
10. Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3-configurazione della fotocamera principale

> [!IMPORTANT]
> Se si desidera ignorare il componente *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile [scaricarlo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo nel progetto come [*pacchetto personalizzato*](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-results-class). Sarà comunque necessario creare un progetto Unity.

1.  Nel *Pannello gerarchia*è presente un oggetto denominato **Main camera**, che rappresenta il punto di visualizzazione "Head" dopo che l'applicazione è stata "interna".
2.  Con il dashboard Unity in primo piano, selezionare la **fotocamera principale GameObject**. Si noterà che il *pannello Inspector* , disponibile in genere a destra, all'interno del dashboard, visualizzerà i vari componenti di tale *GameObject*, con la *trasformazione* nella parte superiore, seguita dalla *fotocamera*e da altri componenti. Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che venga posizionata correttamente.
3.  A tale scopo, selezionare l'  icona dell'ingranaggio accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**. 

    ![Reimposta la trasformazione della fotocamera principale.](images/AzureLabs-Lab1-19.png)
 
4.  Il componente *Transform* dovrebbe essere simile al seguente:

    1. La *posizione* è impostata su **0, 0, 0**
    2. *Rotation* è impostato su **0, 0, 0**
    3. E  la scalabilità è impostata su **1, 1, 1**

        ![Trasforma informazioni per la fotocamera](images/AzureLabs-Lab1-20.png)

5.  Quindi, con l'oggetto **principale della fotocamera** selezionato, vedere il pulsante **Aggiungi componente** che si trova nella parte inferiore del *pannello Inspector*. 
6.  Selezionare tale pulsante e cercare (digitando *origine audio* nel campo di ricerca o spostandosi nelle sezioni) per il componente denominato **origine audio** , come illustrato di seguito, e selezionarlo (premendo invio anche in questo caso).
7.  Un componente di *origine audio* verrà aggiunto alla **fotocamera principale**, come illustrato di seguito.

    ![Aggiungere un componente di origine audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Per Microsoft HoloLens, è necessario modificare anche quanto segue, che fa parte del componente della **fotocamera** della **fotocamera principale**:
    > - **Cancella flag:** Colore a tinta unita.
    > - **Informazioni preliminari** ' Black, Alpha 0'-colore esadecimale: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capitolo 4: installazione dell'area di disegno debug

Per visualizzare l'input e l'output della traduzione, è necessario creare un'interfaccia utente di base. Per questo corso, verrà creato un oggetto dell'interfaccia utente Canvas con diversi oggetti ' text ' per visualizzare i dati.

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, in **interfaccia utente**, Aggiungi un'area di **disegno**.

    ![Aggiungere un nuovo oggetto interfaccia utente Canvas.](images/AzureLabs-Lab1-22.png)

2.  Con l'oggetto Canvas selezionato, nel *pannello Inspector* (nel componente "canvas") modificare la modalità di **rendering** in **spazio globale**. 
3.  Modificare quindi i parametri seguenti nella *trasformazione Rect del pannello di controllo*:

    1. *POS*    X 0 Y 0 Z 40 -  
    2. *Larghezza* -500
    3. *Altezza* -300
    4. *Scala*    X 0,13 Y 0,13 Z 0,13 - 

        ![Aggiornare la trasformazione Rect per l'area di disegno.](images/AzureLabs-Lab1-23.png)
 
4.  Fare clic con il pulsante destro del mouse sull' **area di disegno** nel *Pannello gerarchia*, in **interfaccia utente**e aggiungere un **Pannello**. Questo **Pannello** fornirà uno sfondo al testo che verrà visualizzato nella scena.
5.  Fare clic con il pulsante destro del mouse sul **Pannello nel** *Pannello gerarchia*in **interfaccia utente**e aggiungere un **oggetto testo**. Ripetere lo stesso processo fino a quando non sono stati creati quattro oggetti testo dell'interfaccia utente in totale (Suggerimento: se è stato selezionato il primo oggetto ' text ', è possibile premere **' Ctrl ' + d''** per duplicarlo, fino a quando non si dispone di quattro in totale). 
6.  Per ogni **oggetto testo**, selezionarlo e utilizzare le tabelle seguenti per impostare i parametri nel *Pannello di controllo*.

    1. Per il componente di *trasformazione Rect* :

        | Nome                   | Trasformazione- *posizione*             | Larghezza      | Altezza    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Per il componente **testo (script)** :


        | Name                   | Testo               | Dimensione carattere    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Stato microfono: | 20           |
        | AzureResponseLabel     | Risposta Web di Azure | 20           |
        | DictationLabel         |   Si è appena detto:   | 20           |
        | TranslationResultLabel |    Traduzione    | 20           |

        ![Immettere i valori corrispondenti per le etichette dell'interfaccia utente.](images/AzureLabs-Lab1-24.png)

    3. Inoltre, applicare lo stile del carattere in grassetto. In questo modo sarà più facile leggere il testo.

        ![Carattere grassetto.](images/AzureLabs-Lab1-25.png)

7.  Per ogni *oggetto testo dell'interfaccia utente* creato nel [capitolo 5](#chapter-5--create-the-results-class), creare un nuovo **oggetto testo dell'interfaccia utente** *figlio* . Questi elementi figlio visualizzeranno l'output dell'applicazione. Creare oggetti *figlio* facendo clic con il pulsante destro del mouse sul padre desiderato, ad esempio *MicrophoneStatusLabel*, e quindi selezionando **interfaccia utente** e quindi selezionando **testo**.
8.  Per ognuno di questi elementi figlio, selezionarlo e utilizzare le tabelle seguenti per impostare i parametri nel pannello di controllo.

    1. Per il componente di **trasformazione Rect** :

        | NOME                  | Trasformazione- *posizione* | Larghezza      | Altezza    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. Per il componente **testo (script)** :

        | Nome                  | Testo          | Dimensione carattere    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Selezionare quindi l'opzione di allineamento "Center" per ogni componente di testo:

    ![Allinea il testo.](images/AzureLabs-Lab1-26.png)

10. Per assicurarsi che gli oggetti **testo dell'interfaccia utente figlio** siano facilmente leggibili, modificarne il *colore*. A tale scopo, fare clic sulla barra (attualmente "nero") accanto a *colore*. 

    ![Immettere i valori corrispondenti per gli output di testo dell'interfaccia utente.](images/AzureLabs-Lab1-27.png)
 
11. Quindi, nella finestra nuovo, piccolo, *colore* , modificare il *colore esadecimale* in: **0032EAFF**

    ![Aggiornare il colore al blu.](images/AzureLabs-Lab1-28.png)
 
12. Di seguito è illustrata l'aspetto dell' **interfaccia utente** .
    1.  Nel *Pannello gerarchia*:

        ![Dispone della gerarchia nella struttura fornita.](images/AzureLabs-Lab1-29.png)

    2.  Nelle viste *scene* e *giochi*:

        ![Includere le viste scene e giochi nella stessa struttura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capitolo 5: creare la classe Results

Il primo script che è necessario creare è la  classe results, che è responsabile di fornire un modo per visualizzare i risultati della conversione. La classe archivia e visualizza quanto segue: 

- Risultato della risposta da Azure.
- Stato del microfono. 
- Risultato della dettatura (Voice to Text).
- Risultato della traslazione.

Per creare questa classe: 

1.  Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**. Denominare gli **script**della cartella. 
 
    ![Crea cartella script.](images/AzureLabs-Lab1-31.png)

    ![Aprire la cartella script.](images/AzureLabs-Lab1-32.png)
 
2.  Con la  cartella Scripts create, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e selezionare **Crea >** quindi  **C# script**. Assegnare un nome ai *risultati*dello script. 

    ![Creare il primo script.](images/AzureLabs-Lab1-33.png)
 
3.  Fare doppio clic sul nuovo script *dei risultati* per aprirlo con **Visual Studio**.
4.  Inserire gli spazi dei nomi seguenti:

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

6.  Aggiungere quindi il metodo *sveglie ()* che verrà chiamato quando la classe viene inizializzata. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Aggiungere infine i metodi che sono responsabili dell'output delle varie informazioni sui risultati nell'interfaccia utente. 

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

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capitolo 6: creare la classe *MicrophoneManager*

La seconda classe che si intende creare è *MicrophoneManager*.

Questa classe è responsabile di:

- Rilevamento del dispositivo di registrazione collegato all'auricolare o al computer (a seconda di quale sia l'impostazione predefinita).
- Acquisire l'audio (voce) e utilizzare la dettatura per archiviarlo come stringa.
- Una volta sospesa la voce, inviare la dettatura alla classe Translator.
- Ospitare un metodo che può arrestare l'acquisizione vocale, se lo si desidera.

Per creare questa classe: 
1.  Fare doppio clic sulla  cartella Scripts per aprirla. 
2.  Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare lo script *MicrophoneManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi in modo che corrispondano a quelli riportati di seguito, all'inizio della classe *MicrophoneManager* :

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *MicrophoneManager* :

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

6.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* . Questi verranno chiamati quando la classe inizializza:

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

7.  È possibile *eliminare* il metodo *Update ()* perché non verrà utilizzato da questa classe.
8.  A questo punto sono necessari i metodi usati dall'app per avviare e arrestare l'acquisizione vocale e passarli alla classe *Translator* , che verrà compilata a breve. Copiare il codice seguente e incollarlo sotto il metodo *Start ()* .

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
    > Anche se questa applicazione non lo userà, il metodo *StopCapturingAudio ()* è stato fornito qui. Se si vuole implementare la possibilità di arrestare l'acquisizione dell'audio nell'applicazione.

9.  A questo punto è necessario aggiungere un gestore di dettatura che verrà richiamato quando la voce viene arrestata. Questo metodo passerà quindi il testo imposto alla classe *Translator* .

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
> A questo punto si noterà un errore nel pannello *console Editor Unity* ("il nome ' Translator ' non esiste..."). Questo perché il codice fa riferimento alla classe *Translator* , che verrà creata nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capitolo 7-chiamata a Azure e al servizio Translator

L'ultimo script che è necessario creare è la classe *Translator* . 

Questa classe è responsabile di:

-   Autenticazione dell'app con *Azure*, in Exchange per un **token di autenticazione**.
-   Usare il **token di autenticazione** per inviare il testo (ricevuto dalla classe *MicrophoneManager* ) da tradurre.
-   Ricevere il risultato tradotto e passarlo alla  classe results da visualizzare nell'interfaccia utente.

Per creare questa classe: 
1.  Passare alla cartella **Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse sul **Pannello del progetto**, quindi **creare > C# script**. Chiamare lo script *Translator*.
3.  Fare doppio clic sul nuovo script di *conversione* per aprirlo **con Visual Studio**.
4.  Aggiungere i seguenti spazi dei nomi all'inizio del file:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *Translator* :

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
    > - Le lingue inserite nell' **enum** di lingue sono solo esempi. Se lo si desidera, è possibile aggiungerne altri. l' [API supporta oltre 60 lingue](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluso Klingon).
    > - Esiste una [pagina più interattiva che copre le lingue disponibili](https://www.microsoft.com/translator/business/languages/), ma è importante tenere presente che la pagina sembra funzionare solo quando la lingua del sito è impostata su "en-US" (e il sito Microsoft verrà probabilmente reindirizzato alla lingua nativa). È possibile modificare la lingua del sito nella parte inferiore della pagina o modificando l'URL.
    > - Il valore **authorizationKey** , nel frammento di codice precedente, deve essere la **chiave** ricevuta quando si è effettuata la sottoscrizione al *API traduzione testuale di Azure*. Questo è stato trattato nel [capitolo 1](#chapter-1--the-azure-portal).

6.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* . 
7.  In questo caso, il codice effettuerà una chiamata ad *Azure* usando la chiave di autorizzazione per ottenere un *token*.

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
    > Il token scadrà dopo 10 minuti. A seconda dello scenario per l'app, potrebbe essere necessario eseguire più volte la stessa chiamata di coroutine.

8.  La coroutine per ottenere il token è la seguente:

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
    > Se si modifica il nome del metodo IEnumerator **GetTokenCoroutine ()** , è necessario aggiornare i valori della stringa di chiamata *StartCoroutine* e *StopCoroutine* nel codice riportato sopra. In base alla [documentazione](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)di Unity, per arrestare una coroutine specifica, è necessario usare il metodo del valore stringa.

9.  Successivamente, aggiungere la coroutine (con un metodo del flusso di "supporto" sotto di essa) per ottenere la traduzione del testo ricevuto dalla classe *MicrophoneManager* . Questo codice crea una stringa di query da inviare al *API traduzione testuale di Azure*, quindi usa la classe UnityWebRequest di Unity interna per effettuare una chiamata Get all'endpoint con la stringa di query. Il risultato viene quindi utilizzato per impostare la traduzione nell'oggetto risultati. Il codice seguente illustra l'implementazione:

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

10. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Capitolo 8: configurare la scena Unity

1.  Nell'editor di Unity fare clic e trascinare la  classe results *dalla* cartella Scripts all'oggetto **principale della fotocamera**  nel *Pannello gerarchia*.
2.  Fare clic sulla **fotocamera principale** ed esaminare il *pannello Inspector*. Si noterà che all'interno del componente *script* appena aggiunto sono presenti quattro campi con valori vuoti. Questi sono i riferimenti di output alle proprietà nel codice. 
3.  Trascinare gli oggetti **testo** appropriati dal *Pannello gerarchia* a questi quattro slot, come illustrato nell'immagine seguente.

    ![Aggiornare i riferimenti di destinazione con i valori specificati.](images/AzureLabs-Lab1-34.png)
  
4.  Quindi, fare clic e trascinare la classe *Translator* dalla  cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*. 
5.  Quindi, fare clic e trascinare la classe *MicrophoneManager* dalla  cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*. 
6.  Infine, fare clic sulla **videocamera principale** ed esaminare il *pannello Inspector*. Si noterà che nello script che è stato trascinato sono presenti due caselle di riepilogo a discesa che consentono di impostare le lingue.
 
    ![Verificare che i linguaggi di traduzione previsti siano di input.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capitolo 9: test in realtà mista

A questo punto è necessario testare che la scena è stata implementata correttamente.

Assicurarsi che:

- Tutte le impostazioni indicate nel [capitolo 1](#chapter-1--the-azure-portal) sono impostate correttamente. 
- I *risultati*, *Translator*e *MicrophoneManager*, gli script sono allegati all'oggetto della **fotocamera principale** . 
- La **chiave** del servizio *API traduzione testuale di Azure* è stata inserita nella variabile **AuthorizationKey** all'interno dello script *Translator* .  
- Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.
- Il microfono funziona quando si esegue la scena. in caso contrario, verificare che il microfono collegato sia il dispositivo *predefinito* e che sia stato [configurato correttamente all'interno di Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10).

È possibile testare l'auricolare immersivo premendo il pulsante **Play** nell'editor di *Unity*.
L'app deve funzionare tramite l'auricolare immersivo collegato.

> [!WARNING]  
> Se nella console di Unity viene visualizzato un errore relativo alla modifica del dispositivo audio predefinito, è possibile che la scena non funzioni come previsto. Questo è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per le cuffie che li hanno. Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e le operazioni dovrebbero funzionare come previsto.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capitolo 10: compilare la soluzione UWP e sideload nel computer locale

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare a **impostazioni di compilazione**: **File > impostazioni di compilazione...**
2.  Nella finestra **impostazioni di compilazione** fare clic su **Compila**.

    ![Compilare la scena Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Se non è già stato fatto, è necessario che i **progetti C# Unity**
4.  Fai clic su **Compila**. Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla *app*. Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella cartella dell' *app* . 
6.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-11--deploy-your-application"></a>Capitolo 11-distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.
2.  Nella configurazione della soluzione selezionare **debug**.
3.  Nella piattaforma soluzione selezionare **x86**, **computer locale**. 

    > Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer. Tuttavia, sarà necessario eseguire anche le operazioni seguenti:
    > - Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Verificare che la *modalità sviluppatore* sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per SIDELOAD l'applicazione al PC.
5.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.
6.  Una volta avviata, l'app richiederà di autorizzare l'accesso al microfono. Assicurarsi di fare clic sul pulsante **Sì** .
7.  A questo punto è possibile iniziare a tradurre.

## <a name="your-finished-translation-text-api-application"></a>Applicazione API testo traduzione completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta l'API traduzione testuale di Azure per convertire il riconoscimento vocale in testo tradotto.

![Prodotto finale.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

È possibile aggiungere funzionalità di sintesi vocale all'app, in modo che il testo restituito venga pronunciato?

### <a name="exercise-2"></a>Esercizio 2

Consentire all'utente di modificare le lingue di origine e di output ("da" e "in") nell'app stessa, in modo che l'app non debba essere ricompilata ogni volta che si desidera modificare le lingue.
