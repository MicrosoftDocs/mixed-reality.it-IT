---
title: Input MR 210 - sguardo
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate su concetti sguardo di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sguardo dell'esercitazione, academy,
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599373"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-input-210-gaze"></a>Input di MR 210: Sguardo fisso

[Estasiati](gaze.md) è il primo modulo di input e rivela consapevolezza e finalità dell'utente. 210 Input MR (noto anche come Esplora progetti) è un'analisi approfondita i concetti correlati sguardo per realtà mista di Windows. Verranno aggiunte consapevolezza contestuale per il cursore e vntana, sfruttando al meglio ciò che l'app conosce sguardo dell'utente.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Abbiamo un astronautici descrittivo qui per scoprire i concetti sguardo. Nelle [MR nozioni di base 101](holograms-101.md), avevamo un cursore semplice seguite semplicemente lo sguardo. Oggi passiamo ora spinge ulteriormente oltre con il cursore semplice:

* Rendiamo il cursore e i nostri vntana sguardo riconoscere: entrambi cambierà in base a dove sta guardando l'utente - o in cui l'utente viene *non* alla ricerca. Questo li rende sensibili al contesto.
* Si aggiungerà commenti e suggerimenti a cursore e vntana per consentire all'utente altre informazioni sul contesto su ciò che è interessato. Questi commenti e suggerimenti possono essere audio e video.
* Ti mostreremo le tecniche di destinazione per consentire agli utenti di raggiungere destinazioni più piccole.
* Vi mostreremo come attirare l'attenzione dell'utente di vntana con un indicatore direzionale.
* Si saranno di apprendere rapidamente le tecniche per sfruttare il vntana con l'utente come Anna non si sposta il mondo.

>[!IMPORTANT]
>I video incorporati in ognuna delle sezioni seguenti sono stati registrati usando una versione precedente di Unity e il Toolkit di realtà mista. Anche se le istruzioni dettagliate sono accurate e aggiornate, è possibile visualizzare gli script e gli oggetti visivi nei video corrispondenti che non sono aggiornati. I video rimangono inclusi per ci si ricorderà più e perché i concetti illustrati sono applicano.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Input di MR 210: Sguardo fisso</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).
* Alcuni basic C# capacità di programmazione.
* È necessario avere completato [MR nozioni di base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errori e note

* In Visual Studio, "Just My Code" deve essere disabilitata (deselezionata) in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1 - il programma di installazione di Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Obiettivi

* L'ottimizzazione di Unity per lo sviluppo di HoloLens.
* Importare le risorse e configurare la scena.
* Visualizzare l'astronautici di HoloLens.

### <a name="instructions"></a>Istruzioni

1. Avviare Unity.
2. Selezionare **nuovo progetto**.
3. Denominare il progetto **ModelExplorer**.
4. Immettere il percorso come il **estasiati** cartella è archiviato in precedenza di annullamento.
5. Verificare che il progetto è impostato su **3D**.
6. Fare clic su **Crea progetto**.

### <a name="unity-settings-for-hololens"></a>Impostazioni di Unity per HoloLens

Dobbiamo informare Unity che deve creare l'app è in corso per esportare un' [vista immersiva](app-views.md) invece di una visualizzazione 2D. Ciò si ottiene aggiungendo HoloLens come dispositivo di realtà virtuale.

1. Passare a **Modifica > impostazioni del progetto > Player**.
2. Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.
3. Espandere la **XR impostazioni** gruppo.
4. Nel **Rendering** sezione controllo la **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **gli SDK di realtà virtuale** elenco.
5. Verificare che **realtà mista di Windows** visualizzato nell'elenco. In caso contrario, selezionare la **+** pulsante nella parte inferiore dell'elenco e scegliere **Windows Holographic**.

Successivamente, è necessario impostare scripting back-end per .NET.

1. Passare a **Modifica > Impostazioni di progetto > Player** (è ancora possibile avere questo nel passaggio precedente).
2. Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.
3. Nel **altre impostazioni** Configuration sezione, assicurarsi che **Scripting back-end** è impostato su **.NET**

Infine, aggiorneremo le impostazioni di qualità per ottenere una rapida prestazioni su HoloLens.

1. Passare a **Modifica > impostazioni del progetto > qualità**.
2. Fare clic sulla freccia rivolta nel **predefinito** riga sotto l'icona di Windows Store.
3. Selezionare **veloce** per **le app di Windows Store**.

### <a name="import-project-assets"></a>Importare le risorse del progetto

1. Fare clic il **asset** cartella il **progetto** pannello.
2. Fare clic su **Importa pacchetto > pacchetto personalizzato**.
3. Passare ai file di progetto è stato scaricato e fare clic su **ModelExplorer.unitypackage**.
4. Fare clic su **Apri**.
5. Dopo avere caricato il pacchetto, fare clic sui **importazione** pulsante.

### <a name="setup-the-scene"></a>Programma di installazione della scena

1. Nella gerarchia, eliminare il **Main Camera**.
2. Nel **HoloToolkit** cartella, aprire il **Input** cartella, quindi aprire il **Prefabs** cartella.
3. Trascinare e rilasciare il **MixedRealityCameraParent** prefab dal **Prefabs** nella cartella la **gerarchia**.
4. Fare doppio clic il **luce direzionale** nella gerarchia e selezionare **eliminare**.
5. Nel **Vntana** cartella, trascinare e rilasciare le risorse seguenti nella radice del **gerarchia**:
    * **AstroMan**
    * **luci**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Avviare **modalità di riproduzione** ▶ per visualizzare l'astronautici.
7. Fare clic su **modalità di riproduzione** ▶ nuovamente a **arrestare**.
8. Nel **Vntana** cartella trovare il **Fitbox** asset e trascinarlo nella radice del **gerarchia**.
9. Selezionare il **Fitbox** nel **gerarchia** pannello.
10. Trascinare il **AstroMan** raccolta dal **gerarchia** per il **raccolta ologrammi** proprietà del Fitbox nel **Inspector** pannello.

### <a name="save-the-project"></a>Salvare il progetto

1. Salvare la nuova scena: **File > Salva scena come**.
2. Fare clic su **nuova cartella** e denominare la cartella **scene**.
3. Denominare il file "**ModelExplorer**" e salvarlo nel **scene** cartella.

### <a name="build-the-project"></a>Compilare il progetto

1. In Unity, selezionare **File > Build Settings**.
2. Fare clic su **aggiungere scene Open** per aggiungere la scena.
3. Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.
4. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**. In caso contrario, ci si trova sulla **tutti i dispositivi**.
5. Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).
6. Fai clic su **Compila**.
7. Creare un **nuova cartella** denominato "App".
8. Solo clic i **App** cartella.
9. Premere **Seleziona cartella**.

Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.

1. Aprire il **App** cartella.
2. Aprire il **soluzione ModelExplorer Visual Studio**.

Se la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.
2. Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**. Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.
4. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**. Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Quando l'app è distribuita, ignorare il **Fitbox** con un **movimento selezionare**.

Se la distribuzione in un visore VR immersivi:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione è impostata su **computer locale**.
3. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
4. Quando l'app è distribuita, ignorare il **Fitbox** spostando il trigger in un controller di movimento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capitolo 2 - commenti e suggerimenti del cursore e di destinazione

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Obiettivi

* Progettazione visiva del cursore e il comportamento.
* Commenti e suggerimenti basati su sguardo cursore.
* Commenti e suggerimenti basati su sguardo ologramma.

Si vuole basare il lavoro su principi di progettazione del cursore, vale a dire:

* Il cursore è sempre presente.
* Non farti cursore troppo piccola o grande.
* Evitare ostruendo contenuto.

### <a name="instructions"></a>Istruzioni

1. Nel **HoloToolkit\Input\Prefabs** cartella trovare il **InputManager** asset.
2. Trascinare e rilasciare il **InputManager** nel **gerarchia**.
3. Nel **HoloToolkit\Input\Prefabs** cartella trovare il **cursore** asset.
4. Trascinare e rilasciare il **cursore** nel **gerarchia**.
5. Selezionare il **InputManager** dell'oggetto nel **gerarchia**.
6. Trascinare il **cursore** dell'oggetto dal **gerarchia** nel InputManager **SimpleSinglePointerSelector**del **cursore** campo, nel nella parte inferiore del **Inspector**.

![Configurazione di selettore singolo puntatore semplice](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilare e distribuire

1. Ricompilare l'app dalla **File > Impostazioni di compilazione**.
2. Aprire il **cartella App**.
3. Aprire il **soluzione ModelExplorer Visual Studio**.
4. Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.
5. Osservare come viene disegnato il cursore e come cambia aspetto se tocca ologramma.

### <a name="instructions"></a>Istruzioni

1. Nel **gerarchia** panel, espandere il **AstroMan**->**GEO_G**->**Back_Center** oggetto.
2. Fare doppio clic su **Interactible.cs** per aprirlo in Visual Studio.
3. Rimuovere il commento le righe di **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** callback nei **Interactible.cs**. Questi vengono chiamati dal InputManager del Toolkit di realtà mista quando lo stato attivo (sguardo oppure posizionando il controller) entra ed esce dalla collider del GameObject specifico.

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
>Usiamo `EnableKeyword` e `DisableKeyword` sopra. Per rendere utilizzare questi elementi nella tua app con shader Standard del Toolkit, è necessario seguire le [linee guida di Unity per l'accesso ai materiali tramite script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). In questo caso, sono già stati inclusi i [tre varianti di materiale evidenziato](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessari nella cartella delle risorse (cercare le tre prime con evidenziazione nel nome).

### <a name="build-and-deploy"></a>Compilare e distribuire

1. Come in precedenza, compilare il progetto e distribuire il HoloLens.
2. Osservare cosa accade quando lo sguardo è rivolto a un oggetto e se non lo è.

## <a name="chapter-3---targeting-techniques"></a>Capitolo 3 - tecniche come destinazione

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Obiettivi

* Rendono più semplice vntana di destinazione.
* Stabilizzare naturale spostamenti di tipo head.

### <a name="instructions"></a>Istruzioni

1. Nel **gerarchia** riquadro, seleziona la **InputManager** oggetto.
2. Nel **Inspector** panel, trovare il **estasiati stabilizzatore** script. Fare clic per aprirlo in Visual Studio, se si vuole dare un'occhiata.
    * Questo script esegue l'iterazione su campioni di dati Raycast e consente di stabilizzare sguardo dell'utente per specificare come destinazione di precisione.
3. Nel **Inspector**, è possibile modificare le **archiviati esempi stabilità** valore. Questo valore rappresenta il numero di campioni che lo stabilizzatore scorre a calcolare il valore di stabilizzazione.

## <a name="chapter-4---directional-indicator"></a>Capitolo 4 - indicatore direzionale

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Obiettivi

* Aggiungere un indicatore direzionale sul cursore per consentire di individuare vntana.

### <a name="instructions"></a>Istruzioni

Si userà il **DirectionIndicator.cs** file che conterrà:

1. Mostra l'indicatore direzionale se l'utente non è gazing nel vntana.
2. Consente di nascondere l'indicatore direzionale se l'utente è gazing nel vntana.
3. Aggiornare l'indicatore direzionale in modo che punti la vntana.

Cominciamo.

1. Fare clic sui **AstroMan** dell'oggetto nel **gerarchia** pannello e **fare clic sulla freccia** per espanderlo.
2. Nel **gerarchia** pannello, seleziona la **DirectionalIndicator** dell'oggetto sotto **AstroMan**.
3. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
4. Nel menu, digitare nella casella di ricerca **indicatori di direzione**. Selezionare il risultato della ricerca.
5. Nel **gerarchia** del pannello selezionare e trascinare il **cursore** dell'oggetto nel **cursore** proprietà nel **Inspector**.
6. Nel **Project** pannello il **Vntana** cartella, trascinare e rilasciare il **DirectionalIndicator** asset nel **indicatore direzionale**proprietà di **Inspector**.
7. Compilare e distribuire l'app.
8. Guarda come oggetto indicatore direzionale consente di trovare l'astronautici.

## <a name="chapter-5---billboarding"></a>Capitolo 5 - del billboard

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Obiettivi

* Utilizzare del billboard vntana sempre affrontare verso di te.

Verrà usato il **Billboard.cs** file per mantenere un GameObject orientata ai servizi in modo che sia rivolto verso l'utente in qualsiasi momento.

1. Nel **gerarchia** riquadro, seleziona la **AstroMan** oggetto.
2. Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
3. Nel menu, digitare nella casella di ricerca **Billboard**. Selezionare il risultato della ricerca.
4. Nel **Inspector** impostare il **Pivot asse** al **Y**.
5. Prova! Compilare e distribuire l'app come prima.
6. Vedere come l'oggetto pannello volti indipendentemente da come si modifica il punto di vista.
7. Eliminare lo script dal **AstroMan** per il momento.

## <a name="chapter-6---tag-along"></a>Capitolo 6 - Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Obiettivi

* Utilizzare Tag-Along del nostro vntana seguici nella stanza.

Quando si lavora su questo problema, abbiamo informazioni dettagliate tramite i vincoli di progettazione seguenti:

* Contenuto deve essere sempre immediatamente da subito.
* Contenuto non deve essere nel modo.
* Il contenuto di blocco HEAD è disagio.

La soluzione usata in questo esempio consiste nell'utilizzare un approccio "tag-along".

Un oggetto tag-along lascia mai in vista dell'utente. È possibile considerare l'allegato un tag-along come un oggetto all'inizio dell'utente da elastici. Quando l'utente sposta, il contenuto viene mantenuta all'interno di un semplice sguardo facendo scorrere verso il bordo della visualizzazione senza uscire completamente da. Quando l'utente gazes verso l'oggetto tag-along, viene visualizzata più dettagliatamente nella visualizzazione.

Si userà il **SimpleTagalong.cs** file che conterrà:

1. Determinare se l'oggetto Tag-Along è entro i limiti della fotocamera.
2. In caso contrario all'interno del cono di visualizzazione, posizionare il Tag-Along per parzialmente all'interno del cono di visualizzazione.
3. In caso contrario, posizionare il Tag-Along a una distanza predefinita da parte dell'utente.

A tale scopo, è innanzitutto necessario modificare il **Interactible.cs** script per chiamare le **TagalongAction**.

1. Modificare **Interactible.cs** esercitare 6.a (rimozione di commenti linee 84 a 87) al completamento della scrittura di codice.

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Il **InteractibleAction.cs** script, abbinato **Interactible.cs** esegue azioni personalizzate quando si tocca su vntana. In questo caso, si userà uno in particolare per tag-along.

* Nel **gli script** cartella fare clic su **TagalongAction.cs** asset per aprire in Visual Studio.
* Completare l'esercizio di scrittura di codice o sostituirlo con questo:
  * In cima il **gerarchia**, nel tipo di barra di ricerca **ChestButton_Center** e selezionare il risultato.
  * Nel **Inspector** del pannello, fare clic sui **Add Component** pulsante.
  * Nel menu, digitare nella casella di ricerca **abbinato azione**. Selezionare il risultato della ricerca.
  * Nelle **Vntana** cartella trovare il **abbinato** asset.
  * Selezionare il **ChestButton_Center** dell'oggetto nel **gerarchia**. Trascinare e rilasciare il **abbinato** dell'oggetto dal **progetto** pannello il **Inspector** nel **oggetto per abbinato** proprietà.
  * Trascinare il **azione abbinato** dall'oggetto il **Inspector** nel **azione Interactible** campo il **Interactible** script.
* Fare doppio clic il **TagalongAction** script per aprirlo in Visual Studio.

![Configurazione interactible](images/holograms210-interactible.png)

È necessario aggiungere quanto segue:

* Aggiungere funzionalità alla funzione PerformAction nello script TagalongAction (ereditato da InteractibleAction).
* Aggiungere del billboard all'oggetto gazed a una e impostare l'asse di rotazione a dispersione.
* Aggiungere quindi Tag-Along semplice all'oggetto.

Ecco la nostra soluzione, dal **TagalongAction.cs**:

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
* Guarda come il contenuto seguente al centro del punto di sguardo, ma non in modo continuo e senza l'origine del blocco.
