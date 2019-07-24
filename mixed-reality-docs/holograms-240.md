---
title: MR sharing 240-più dispositivi HoloLens
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sulla condivisione degli ologrammi.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, condivisione, rete, Accademia, esercitazione
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522338"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR sharing 240: Più dispositivi HoloLens

Gli ologrammi ricevono una presenza nel nostro mondo rimanendo al posto mentre ci si sposta nello spazio. HoloLens mantiene gli ologrammi sul posto usando vari [sistemi di coordinate](coordinate-systems.md) per tenere traccia della posizione e dell'orientamento degli oggetti. Quando si condividono questi sistemi di coordinate tra i dispositivi, è possibile creare un'esperienza condivisa che ci consenta di partecipare a un mondo olografico condiviso.

In questa esercitazione verrà:

* Configurare una rete per un'esperienza condivisa.
* Condividere gli ologrammi tra i dispositivi HoloLens.
* Scopri altre persone nel nostro mondo olografico condiviso.
* Consente di creare un'esperienza interattiva condivisa in cui è possibile fare riferimento ad altri giocatori e avviare i loro proiettili.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR sharing 240: Più dispositivi HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md) con accesso a Internet.
* Almeno due dispositivi HoloLens configurati [per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
  * Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere. Mantenendo il nome della cartella **SharedHolograms**.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capitolo 1-Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In questo capitolo verrà configurato il primo progetto Unity ed eseguiamo il processo di compilazione e distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per sviluppare app olografiche.
* Vedi l'ologramma!

### <a name="instructions"></a>Istruzioni

* Avvia Unity.
* Selezionare **Apri**.
* Immettere il percorso come cartella **SharedHolograms** precedentemente non archiviata.
* Selezionare **nome progetto** e fare clic su **Seleziona cartella**.
* Nella **gerarchia**, fare clic con il pulsante destro del mouse sulla **fotocamera principale** e scegliere **Elimina**.
* Nella cartella **HoloToolkit-sharing-240/Prefabbricates/camera** trovare la prefabbricata **principale della fotocamera** .
* Trascinare e rilasciare la **fotocamera principale** nella **gerarchia**.
* Nella **gerarchia**fare clic su **Crea** e **Crea vuoto**.
* Fare clic con il pulsante destro del mouse sul nuovo **GameObject** e scegliere **Rinomina**.
* Rinominare GameObject in **ologrammcollection**.
* Selezionare l'  oggetto ologrammcollection nella **gerarchia**.
* Nel **controllo** impostare la **posizione di trasformazione** su: **X 0, Y:-0,25, Z: 2**.
* Nella cartella **olografici** del pannello del **progetto**individuare l'asset **EnergyHub** .
* Trascinare e rilasciare l'oggetto **EnergyHub** dal **pannello progetto** alla **gerarchia** come **elemento figlio di ologrammcollection**.
* Seleziona **File > Salva scena con nome...**
* Assegnare alla scena il nome **SharedHolograms** e fare clic su **Save**.
* Premere il pulsante **Play** in Unity per visualizzare l'anteprima degli ologrammi.
* Premere  Riproduci una seconda volta per arrestare la modalità di anteprima.

**Esportare il progetto da Unity a Visual Studio**
* In Unity selezionare **File > impostazioni di compilazione**.
* Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
* Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
* Impostare **SDK** su **Universal 10**.
* Impostare il **dispositivo di destinazione** su **HoloLens** e il **tipo di compilazione UWP** su **D3D**.
* Controllare **i C# progetti Unity**.
* Fai clic su **Compila**.
* Nella finestra Esplora file visualizzata creare una **nuova cartella** denominata "app".
* Fare clic sulla cartella dell' **app** .
* Premere **Seleziona cartella**.
* Quando si esegue Unity, viene visualizzata una finestra Esplora file.
* Aprire la cartella dell' **app** .
* Aprire **SharedHolograms. sln** per avviare Visual Studio.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
* Fare clic sulla freccia a discesa accanto a computer locale e selezionare **dispositivo remoto**.
    * Impostare l' **Indirizzo** sul nome o sull'indirizzo IP del HoloLens. Se non si conosce l'indirizzo IP del dispositivo, controllare **le impostazioni > rete & Internet > opzioni avanzate** o richiedere a Cortana **"Hey Cortana, qual è il mio indirizzo IP?"**
    * Lasciare la **modalità di autenticazione** impostata su **universale**.
    * Fare clic su **Seleziona**
* Fare clic su **debug > avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Inserire il HoloLens e trovare l'ologramma di EnergyHub.

## <a name="chapter-2---interaction"></a>Capitolo 2-interazione

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In questo capitolo si interagisce con gli ologrammi. Prima di tutto, verrà aggiunto un cursore per visualizzare lo [sguardo](gaze.md). Quindi, aggiungiamo i [movimenti](gestures.md) e usiamo la mano per inserire gli ologrammi nello spazio.

### <a name="objectives"></a>Obiettivi

* Utilizzare l'input di sguardi per controllare un cursore.
* Usare l'input dei movimenti per interagire con gli ologrammi.

### <a name="instructions"></a>Istruzioni

**Sguardo fisso**
* Nel **Pannello gerarchia** selezionare l'oggetto **ologrammcollection** .
* Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .
* Nel menu digitare nella casella di ricerca lo **sguardo Manager**. Selezionare il risultato della ricerca.
* Nella cartella **HoloToolkit-sharing-240\Prefabs\Input** trovare il **cursore** asset.
* Trascinare e rilasciare l'asset del **cursore** nella **gerarchia**.

**Gesto**
* Nel **Pannello gerarchia** selezionare l'oggetto **ologrammcollection** .
* Fare clic su **Aggiungi componente** e digitare **gestione movimenti** nel campo di ricerca. Selezionare il risultato della ricerca.
* Nel **Pannello gerarchia**espandere ologrammcollection .
* Selezionare l'oggetto **EnergyHub** figlio.
* Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .
* Nel menu digitare nella casella di ricerca **posizionamento ologrammi**. Selezionare il risultato della ricerca.
* Salvare la scena selezionando **File > Salva scena**.

**Distribuisci e goditi**
* Eseguire la compilazione e la distribuzione nella HoloLens usando le istruzioni del capitolo precedente.
* Una volta avviata l'app nella HoloLens, sposta la tua parte e osserva il modo in cui il EnergyHub segue il tuo sguardo.
* Si noti come viene visualizzato il cursore quando si guarda l'ologramma e si passa a una luce puntiforme senza guardare un ologramma.
* Eseguire un tocco aereo per posizionare l'ologramma. Al momento del progetto, è possibile inserire l'ologramma una sola volta (Ridistribuisci per riprovare).

## <a name="chapter-3---shared-coordinates"></a>Capitolo 3-Coordinate condivise

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

È divertente vedere e interagire con gli ologrammi, ma andiamo oltre. Verrà configurata la prima esperienza condivisa, ovvero un ologramma che tutti gli utenti possono vedere insieme.

### <a name="objectives"></a>Obiettivi

* Configurare una rete per un'esperienza condivisa.
* Stabilire un punto di riferimento comune.
* Condividere i sistemi di coordinate tra dispositivi.
* Tutti gli utenti vedono lo stesso ologramma!

>[!NOTE]
>Per la connessione di un'app al server di condivisione, è necessario dichiarare le funzionalità **InternetClientServer** e **PrivateNetworkClientServer** . Questa operazione viene eseguita per gli ologrammi 240, ma è necessario tenerla presente per i propri progetti.
>1. Nell'editor di Unity passare a Impostazioni lettore passando a "Modifica > Impostazioni progetto > lettore"
>2. Fare clic sulla scheda "Windows Store"
>3. Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità **InternetClientServer** e la funzionalità **PrivateNetworkClientServer**

### <a name="instructions"></a>Istruzioni

* Nel **Pannello del progetto** passare alla cartella **HoloToolkit-sharing-240\Prefabs\Sharing**
* Trascinare e rilasciare il prefabbricato di **condivisione** nel **Pannello gerarchia**.

Successivamente, è necessario avviare il servizio di condivisione. È necessario eseguire questo passaggio solo per **un PC** nell'esperienza condivisa.
* In Unity-nel menu in alto a destra selezionare il **menu HoloToolkit-sharing-240**.
* Selezionare l'elemento **avvio condivisione servizio** nell'elenco a discesa.
* Selezionare l'opzione **rete privata** e fare clic su **Consenti accesso** quando viene visualizzato il prompt del firewall.
* Annotare l'indirizzo IPv4 visualizzato nella finestra della console del servizio di condivisione. Si tratta dello stesso IP del computer in cui viene eseguito il servizio.

Seguire le istruzioni restanti in **tutti i PC** che faranno parte dell'esperienza condivisa.
* Nella **gerarchia**selezionare l'oggetto di **condivisione** .
* In **controllo**, nel componente **fase di condivisione** , modificare l' **indirizzo del server** da "localhost" all'indirizzo IPv4 del computer che esegue SharingService. exe.
* Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .
* Nel **controllo** fare clic sul pulsante **Aggiungi componente** .
* Nella casella di ricerca digitare **Import Export Anchor Manager**. Selezionare il risultato della ricerca.
* Nel **pannello progetto** passare alla cartella **script** .
* Fare doppio clic sullo script **HologramPlacement** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Tornare in Unity, selezionare **ologrammcollection** nel **Pannello gerarchia**.
* Nel **Pannello di controllo** fare clic sul pulsante **Aggiungi componente** .
* Nel menu digitare nella casella di ricerca **Gestione stato app**. Selezionare il risultato della ricerca.

**Distribuisci e goditi**
* Compilare il progetto per i dispositivi HoloLens.
* Designare un HoloLens per la distribuzione iniziale. È necessario attendere che il punto di ancoraggio venga caricato nel servizio prima di poter inserire il EnergyHub (questa operazione può richiedere circa 30-60 secondi). Fino al termine del caricamento, i movimenti Tap verranno ignorati.
* Dopo aver inserito il EnergyHub, il relativo percorso verrà caricato nel servizio ed è quindi possibile distribuirlo a tutti gli altri dispositivi HoloLens.
* Quando una nuova HoloLens viene aggiunta per la prima volta alla sessione, il percorso di EnergyHub potrebbe non essere corretto nel dispositivo. Tuttavia, non appena i percorsi di ancoraggio e EnergyHub sono stati scaricati dal servizio, EnergyHub dovrebbe passare al nuovo percorso condiviso. Se questo non avviene entro ~ 30-60 secondi, passare alla posizione in cui si trovava il HoloLens originale durante l'impostazione dell'ancoraggio per raccogliere più indizi sull'ambiente. Se il percorso non è ancora bloccato, ridistribuirlo nel dispositivo.
* Quando i dispositivi sono tutti pronti ed eseguono l'app, cercare il EnergyHub. È possibile accordare tutti sulla posizione dell'ologramma e sulla direzione del testo.

## <a name="chapter-4---discovery"></a>Capitolo 4-individuazione

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Tutti gli utenti possono ora visualizzare lo stesso ologramma! A questo punto, vediamo tutti gli altri utenti connessi al nostro mondo olografico condiviso. In questo capitolo si otterrà la posizione della testa e la rotazione di tutti gli altri dispositivi HoloLens nella stessa sessione di condivisione.

### <a name="objectives"></a>Obiettivi

* Scopri le altre nell'esperienza condivisa.
* Scegliere e condividere un avatar del lettore.
* Alleghi l'avatar del lettore accanto alle intestazioni di tutti.

### <a name="instructions"></a>Istruzioni

* Nel **Pannello del progetto** passare alla cartella **ologrammi** .
* Trascinare e rilasciare **PlayerAvatarStore** nella **gerarchia**.
* Nel **pannello progetto** passare alla cartella **script** .
* Fare doppio clic sullo script **AvatarSelector** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .
* Nel **controllo** fare clic su **Aggiungi componente**.
* Nella casella di ricerca digitare **local Player Manager**. Selezionare il risultato della ricerca.
* Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .
* Nel **controllo** fare clic su **Aggiungi componente**.
* Nella casella di ricerca digitare **Remote Player Manager**. Selezionare il risultato della ricerca.
* Aprire lo script **HologramPlacement** in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Aprire lo script **AppStateManager** in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Distribuisci e goditi**
* Compilare e distribuire il progetto nei dispositivi HoloLens.
* Quando si sente un suono di ping, trovare il menu di selezione avatar e selezionare un avatar con il gesto di tocco.
* Se non si stanno esaminando gli ologrammi, la luce puntiforme intorno al cursore diventerà un colore diverso quando il HoloLens comunica con il servizio: inizializzazione (viola scuro), download dell'ancoraggio (verde), importazione/esportazione dei dati della località (giallo), caricamento dell'ancoraggio (blu). Se la luce puntiforme intorno al cursore è il colore predefinito (viola chiaro), si è pronti per interagire con gli altri giocatori della sessione.
* Esaminare gli altri utenti connessi allo spazio. ci sarà un robot olografico che si trova al di sopra della spalla e mima i movimenti della testa.

## <a name="chapter-5---placement"></a>Capitolo 5-selezione host

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In questo capitolo si farà in modo che l'ancoraggio possa essere inserito in superfici reali. Verranno usate le coordinate condivise per posizionare l'ancoraggio nel punto intermedio tra tutti gli utenti connessi all'esperienza condivisa.

### <a name="objectives"></a>Obiettivi

* Posizionare gli ologrammi sulla mappa spaziale in base alla posizione della testa dei giocatori.

### <a name="instructions"></a>Istruzioni

* Nel **Pannello del progetto** passare alla cartella **ologrammi** .
* Trascinare e rilasciare il prefabbricato **CustomSpatialMapping** nella **gerarchia**.
* Nel **pannello progetto** passare alla cartella **script** .
* Fare doppio clic sullo script **AppStateManager** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* Nel **pannello progetto** passare alla cartella **script** .
* Fare doppio clic sullo script **HologramPlacement** per aprirlo in Visual Studio.
* Sostituire il contenuto con il codice seguente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Distribuisci e goditi**
* Compilare e distribuire il progetto nei dispositivi HoloLens.
* Quando l'app è pronta, si trova in un cerchio e si noterà che il EnergyHub viene visualizzato al centro di tutti.
* Toccare per inserire il EnergyHub.
* Provare il comando vocale ' Reimposta destinazione ' per selezionare il EnergyHub di backup e collaborare come gruppo per spostare l'ologramma in una nuova posizione.

## <a name="chapter-6---real-world-physics"></a>Capitolo 6-fisica reale

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In questo capitolo verranno aggiunti gli ologrammi che rimbalzano sulle superfici reali. Guarda lo spazio con i progetti avviati dall'utente e dai tuoi amici.

### <a name="objectives"></a>Obiettivi

* Avvia i proiettili che rimbalzano sulle superfici reali.
* Condividere i proiettili in modo che possano essere visualizzati da altri lettori.

### <a name="instructions"></a>Istruzioni

* Nella **gerarchia** selezionare l'oggetto **ologrammcollection** .
* Nel **controllo** fare clic su **Aggiungi componente**.
* Nella casella di ricerca digitare **avvio**del proiettile. Selezionare il risultato della ricerca.

**Distribuisci e goditi**
* Compilare e distribuire nei dispositivi HoloLens.
* Quando l'app è in esecuzione in tutti i dispositivi, è possibile eseguire un rubinetto d'aria per avviare il proiettile su superfici reali.
* Scopri cosa accade quando il proiettile si scontra con l'avatar di un altro giocatore.

## <a name="chapter-7---grand-finale"></a>Capitolo 7-finale finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In questo capitolo viene individuato un portale che può essere individuato solo con la collaborazione.

### <a name="objectives"></a>Obiettivi

* Collaborare per avviare un numero sufficiente di proiettili nell'ancoraggio per individuare un portale segreto.

### <a name="instructions"></a>Istruzioni

* Nel **Pannello del progetto** passare alla cartella **ologrammi** .
* Trascinare e rilasciare l'  asset di Sottomondo come **figlio di ologrammcollection**.
* Con **ologrammcollection** selezionato, fare clic sul pulsante **Aggiungi componente** nel **controllo**.
* Nel menu digitare nella casella di ricerca **ExplodeTarget**. Selezionare il risultato della ricerca.
* Con **ologrammcollection** selezionato, dalla **gerarchia** trascinare l'oggetto **EnergyHub** nel campo di **destinazione** nel **controllo**.
* Con  l'oggetto ologrammcollection selezionato, **dalla gerarchia** trascinare l'oggetto di Sottomondo nel campo Sottomondo del **controllo**.

**Distribuisci e goditi**
* Compilare e distribuire nei dispositivi HoloLens.
* Quando l'app è stata avviata, collaborare insieme per avviare i proiettili nella EnergyHub.
* Quando viene visualizzato il Sottomondo, avviare i proiettili nei robot di Sottomondo (raggiungere un robot tre volte per divertirsi).
