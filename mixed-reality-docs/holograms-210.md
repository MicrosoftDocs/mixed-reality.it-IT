---
title: Input MR 210-sguardo
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi a sguardi.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, sguardo
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993550"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-input-210-gaze"></a>Input MR 210: Sguardo fisso

Lo [sguardo](gaze.md) è la prima forma di input e rivela le finalità e la consapevolezza dell'utente. MR input 210 (noto anche come Project Explorer) è un approfondimento dei concetti correlati a sguardi per la realtà mista di Windows. Verrà aggiunta la consapevolezza contestuale al cursore e agli ologrammi, sfruttando appieno i vantaggi offerti dall'app per quanto riguarda lo sguardo dell'utente.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Qui è disponibile un astronauta che consente di apprendere i concetti di sguardi. In [Mr nozioni di base 101](holograms-101.md), abbiamo un semplice cursore che ha subito seguito lo sguardo. Oggi stiamo muovendo un passaggio oltre il semplice cursore:

* Il cursore e i nostri ologrammi sono consapevoli del fatto che entrambi cambieranno in base alla posizione dell'utente o alla posizione in cui l'utente *non* è in Cerca. Che li rende compatibili con il contesto.
* Si aggiungeranno commenti e suggerimenti al cursore e agli ologrammi per fornire all'utente un maggior contesto sugli elementi di destinazione. Questo feedback può essere costituito da audio e oggetti visivi.
* Verranno illustrate le tecniche di destinazione per aiutare gli utenti a raggiungere obiettivi più piccoli.
* Verrà illustrato come attirare l'attenzione dell'utente sugli ologrammi con un indicatore direzionale.
* Ti insegneremo le tecniche per portare gli ologrammi all'utente mentre si sposta in tutto il mondo.

>[!IMPORTANT]
>I video incorporati in ognuno dei capitoli seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Sebbene le istruzioni dettagliate siano accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti non aggiornati. I video rimangono inclusi per i posteri e perché i concetti trattati sono ancora validi.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 210: Sguardo fisso</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Alcune funzionalità C# di programmazione di base.
* Sono state completate le nozioni di [base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errori e note

* In Visual Studio, "Just My Code" deve essere disabilitato (deselezionato) in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1-installazione di Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per lo sviluppo di HoloLens.
* Importare gli asset e configurare la scena.
* Visualizzare l'astronauta nella HoloLens.

### <a name="instructions"></a>Istruzioni

1. Avvia Unity.
2. Selezionare **nuovo progetto**.
3. Denominare il progetto **ModelExplorer**.
4. Immettere location come cartella degli **sguardi** precedentemente non archiviata.
5. Assicurati che il progetto sia impostato su **3D**.
6. Fai clic su **Create Project** (Crea progetto).

### <a name="unity-settings-for-hololens"></a>Impostazioni Unity per HoloLens

È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D. Questa operazione viene eseguita aggiungendo HoloLens come dispositivo di realtà virtuale.

1. Passare a **Edit > Settings Project > Player**.
2. Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .
3. Espandere il gruppo di **Impostazioni XR** .
4. Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **SDK di realtà virtuale** .
5. Verificare che l'opzione **realtà mista di Windows** sia presente nell'elenco. In caso contrario, selezionare **+** il pulsante nella parte inferiore dell'elenco e scegliere **Windows olografico**.

Successivamente, è necessario impostare il back-end di scripting su .NET.

1. Passare a **Edit > Settings (Impostazioni progetto) > Player** (è possibile continuare a eseguire questa operazione dal passaggio precedente).
2. Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .
3. Nella sezione **altre impostazioni** di configurazione, assicurarsi che **lo scripting backend** sia impostato su **.NET** .

Infine, verranno aggiornate le impostazioni di qualità per ottenere prestazioni rapide su HoloLens.

1. Passare a **modifica > impostazioni progetto > qualità**.
2. Fare clic sulla freccia rivolta verso il basso nella riga **predefinita** sotto l'icona di Windows Store.
3. Selezionare **molto basso** per le **app di Windows Store**.

### <a name="import-project-assets"></a>Importa asset progetto

1. Fare clic con  il pulsante destro del mouse sulla cartella assets nel pannello **Project** .
2. Fare clic su **Importa pacchetto > pacchetto personalizzato**.
3. Individuare i file di progetto scaricati e fare clic su **ModelExplorer. file unitypackage Tools**.
4. Fare clic su **Apri**.
5. Al termine del caricamento del pacchetto, fare clic sul pulsante **Importa** .

### <a name="setup-the-scene"></a>Configurare la scena

1. Nella gerarchia eliminare la **fotocamera principale**.
2. Nella cartella **HoloToolkit** aprire la cartella di **input** , quindi aprire la cartella  prefabbricates.
3. Trascinare il prefabbricato **MixedRealityCameraParent** dalla cartella  prefabbricates alla **gerarchia**.
4. Fare clic con il pulsante destro del mouse sulla **luce direzionale** nella gerarchia e scegliere **Elimina**.
5. Nella cartella **ologrammi** trascinare e rilasciare gli asset seguenti nella radice della **gerarchia**:
    * **AstroMan**
    * **Luci**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Avviare la **modalità di riproduzione** ▶ per visualizzare l'astronauta.
7. Fare clic su **modalità** riproduci ▶ per **arrestare**.
8. Nella cartella **ologrammi** individuare l'asset **fitbox** e trascinarlo nella radice della **gerarchia**.
9. Selezionare **fitbox** nel pannello **gerarchia** .
10. Trascinare la  raccolta astror dalla **gerarchia** alla proprietà della **raccolta ologramma** di fitbox nel pannello **Inspector** .

### <a name="save-the-project"></a>Salvare il progetto

1. Salvare la nuova scena: **File > Salva scena come**.
2. Fare clic su **nuova cartella** e denominare la cartella **Scenes**.
3. Denominare il file "**ModelExplorer**" e salvarlo nella cartella **Scenes** .

### <a name="build-the-project"></a>Compilare il progetto

1. In Unity selezionare **File > impostazioni di compilazione**.
2. Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
3. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
4. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **qualsiasi dispositivo**.
5. Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).
6. Fai clic su **Compila**.
7. Creare una **nuova cartella** denominata "app".
8. Fare clic sulla cartella dell' **app** .
9. Premere **Seleziona cartella**.

Quando si esegue Unity, viene visualizzata una finestra Esplora file.

1. Aprire la cartella dell' **app** .
2. Aprire la **soluzione ModelExplorer di Visual Studio**.

Se si esegue la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
2. Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** . Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.
4. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando l'app è stata distribuita, chiudere il **fitbox** con un **movimento di selezione**.

Se si esegue la distribuzione in un auricolare immersivo:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione sia impostata su **computer locale**.
3. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
4. Quando l'app è stata distribuita, chiudere il **fitbox** estraendo il trigger in un controller di movimento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capitolo 2-feedback del cursore e della destinazione

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Obiettivi

* Comportamento e progettazione visivi del cursore.
* Feedback del cursore basato su sguardi.
* Feedback dell'ologramma basato su sguardi.

Il nostro lavoro verrà basato sui principi di progettazione dei cursori, vale a dire:

* Il cursore è sempre presente.
* Non lasciare il cursore troppo piccolo o grande.
* Evitare di ostacolare il contenuto.

### <a name="instructions"></a>Istruzioni

1. Nella cartella **HoloToolkit\Input\Prefabs** trovare l'asset **InputManager** .
2. Trascinare e rilasciare **InputManager** nella **gerarchia**.
3. Nella cartella **HoloToolkit\Input\Prefabs** trovare il **cursore** asset.
4. Trascinare e rilasciare il **cursore** nella **gerarchia**.
5. Consente di selezionare l'oggetto **InputManager** nella **gerarchia**.
6. Trascinare l'oggetto **cursore** dalla **gerarchia** nel campo **cursore** di **SimpleSinglePointerSelector**di InputManager, nella parte inferiore del **controllo**.

![Configurazione semplice del selettore con puntatore singolo](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Ricompilare l'app da **File > impostazioni di compilazione**.
2. Aprire la **cartella dell'app**.
3. Aprire la **soluzione ModelExplorer di Visual Studio**.
4. Fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.
5. Osservare il modo in cui viene disegnato il cursore e il modo in cui cambia aspetto se tocca un ologramma.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **gerarchia** espandere l'oggetto ->Astron**GEO_G**->**Back_Center** .
2. Fare doppio clic su **Interactible.cs** per aprirlo in Visual Studio.
3. Rimuovere il commento dalle righe nei callback **IFocusable. OnFocusEnter ()** e **IFocusable. OnFocusExit ()** in **Interactible.cs**. Questi vengono chiamati dal InputManager del Toolkit di realtà mista quando lo stato attivo (tramite sguardo o con il puntatore del controller) entra e esce dall'oggetto Collider di GameObject specifico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>`EnableKeyword` Usiamo e `DisableKeyword` versioni successive. Per usarle nella propria app con lo shader standard del Toolkit, è necessario seguire le [linee guida di Unity per accedere ai materiali tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). In questo caso sono già state incluse le [tre varianti del materiale evidenziato](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessario nella cartella Resources (ricerca dei tre materiali con evidenziazione nel nome).

### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. Come in precedenza, compilare il progetto e distribuirlo in HoloLens.
2. Osservare cosa accade quando lo sguardo è mirato a un oggetto e in caso contrario.

## <a name="chapter-3---targeting-techniques"></a>Capitolo 3-tecniche di targeting

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Obiettivi

* Semplificare la destinazione degli ologrammi.
* Stabilizzare i movimenti della testa naturale.

### <a name="instructions"></a>Istruzioni

1. Nel pannello **gerarchia** selezionare l'oggetto **InputManager** .
2. Nel pannello **Inspector** trovare lo script stabilizzatore dello **sguardo** . Fare clic su di esso per aprirlo in Visual Studio, se si vuole dare un'occhiata.
    * Questo script scorre gli esempi di dati di Raycast e consente di stabilizzare lo sguardo dell'utente per la destinazione della precisione.
3. Nel **controllo**è possibile modificare il valore dei **campioni di stabilità archiviati** . Questo valore rappresenta il numero di campioni di cui lo stabilizzatore esegue l'iterazione per calcolare il valore stabilizzato.

## <a name="chapter-4---directional-indicator"></a>Capitolo 4-indicatore direzionale

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Obiettivi

* Aggiungere un indicatore direzionale sul cursore per individuare gli ologrammi.

### <a name="instructions"></a>Istruzioni

Verrà usato il file **DirectionIndicator.cs** che:

1. Mostra l'indicatore direzionale se l'utente non sta guardando gli ologrammi.
2. Nascondere l'indicatore direzionale se l'utente sta guardando gli ologrammi.
3. Aggiornare l'indicatore direzionale in modo che punti agli ologrammi.

Ma veniamo al dunque.

1. Fare clic sull'  oggetto astror nel pannello **gerarchia** e **fare clic sulla freccia** per espanderlo.
2. Nel pannello **gerarchia** selezionare l'oggetto **DirectionalIndicator** in Astron .
3. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
4. Nel menu digitare nell' **indicatore di direzione**della casella di ricerca. Selezionare il risultato della ricerca.
5. Nel pannello **gerarchia** trascinare e rilasciare l'oggetto **cursore** sulla proprietà **Cursor** del **controllo**.
6. Nel pannello **progetto** , nella cartella **ologrammi** , trascinare l'asset **DirectionalIndicator** sulla proprietà **indicatore direzionale** nel **controllo**.
7. Compilare e distribuire l'app.
8. Osservare come l'oggetto indicatore direzionale aiuta a trovare l'astronauta.

## <a name="chapter-5---billboarding"></a>Capitolo 5-Billboard

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Obiettivi

* Usare il tabellone per fare in modo che gli ologrammi siano sempre volti verso l'utente.

Verrà usato il file **Billboard.cs** per tenere un GameObject orientato in modo che sia sempre attivo per l'utente.

1. Nel pannello **gerarchia** selezionare l'oggetto **Astron** .
2. Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
3. Nel menu digitare nella casella di ricerca **Billboard**. Selezionare il risultato della ricerca.
4. Nel **controllo** impostare l' **asse pivot** su **Y**.
5. Prova! Compilare e distribuire l'app come prima.
6. Scopri in che modo l'oggetto Billboard si presenta indipendentemente dalla modalità di modifica del punto di vista.
7. Eliminare lo script da **astroname** per il momento.

## <a name="chapter-6---tag-along"></a>Capitolo 6-tag-along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Obiettivi

* Usare i tag-along per fare in modo che gli ologrammi ci siano nella stanza.

Quando si lavora su questo problema, verranno illustrati i vincoli di progettazione seguenti:

* Il contenuto deve essere sempre un'occhiata.
* Il contenuto non deve essere nel modo previsto.
* Il contenuto del blocco Head è scomodo.

La soluzione usata in questo articolo prevede l'uso di un approccio "tag-along".

Un oggetto tag-along non lascia completamente la visualizzazione dell'utente. È possibile considerare un tag come un oggetto collegato alla testa dell'utente tramite bande di gomma. Quando l'utente si sposta, il contenuto rimarrà in una semplice occhiata scorrendo verso il bordo della visualizzazione senza uscire completamente. Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo.

Verrà usato il file **SimpleTagalong.cs** che:

1. Determinare se l'oggetto tag-along si trova all'interno dei limiti della fotocamera.
2. Se non è presente nella vista tronco, posizionare il tag-lungo su parzialmente all'interno della vista tronco.
3. In caso contrario, posizionare il tag su una distanza predefinita dall'utente.

Per eseguire questa operazione, è necessario prima di tutto modificare lo script **Interactible.cs** per chiamare **TagalongAction**.

1. Modificare **Interactible.cs** completando il codice esercizio 6. a (rimuovendo il commento dalle righe da 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Lo script **InteractibleAction.cs** , associato a **Interactible.cs** , esegue azioni personalizzate quando si toccano gli ologrammi. In questo caso, verrà usato uno specifico per il tag-along.

* Nella cartella **Scripts** fare clic su **TagalongAction.cs** asset per aprirlo in Visual Studio.
* Completare l'esercizio di codifica o sostituirlo con il seguente:
  * Nella parte superiore della **gerarchia**, nella barra di ricerca digitare **ChestButton_Center** e selezionare il risultato.
  * Nel pannello **Inspector** fare clic sul pulsante **Add Component** .
  * Nel menu digitare nella casella di ricerca **azione Tagalong**. Selezionare il risultato della ricerca.
  * Nella  cartella ologrammi trovare l'asset **Tagalong** .
  * Consente di selezionare l'oggetto **ChestButton_Center** nella **gerarchia**. Trascinare e rilasciare l'oggetto **TagAlong** dal pannello del **progetto** nel **controllo** nella proprietà **oggetto in TagAlong** .
  * Trascinare l'oggetto **azione Tagalong** da **Inspector** nel campo **azione Interactible** nello script **Interactible** .
* Fare doppio clic sullo script **TagalongAction** per aprirlo in Visual Studio.

![Configurazione di Interactible](images/holograms210-interactible.png)

È necessario aggiungere quanto segue:

* Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (Ereditato da InteractibleAction).
* Aggiungere il tabellone all'oggetto guardato su e impostare l'asse pivot su XY.
* Aggiungere quindi un semplice tag insieme all'oggetto.

Ecco la nostra soluzione, di **TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Prova! Compilare e distribuire l'app.
* Osservare il modo in cui il contenuto segue il centro del punto di controllo, ma non continuamente e senza bloccarlo.
