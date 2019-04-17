---
title: MR condivisione 240 - più dispositivi HoloLens
description: Seguire questa procedura dettagliata con Unity, Visual Studio e HoloLens che informazioni dettagliate su condivisione vntana di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, condivisione, rete, academy, esercitazione
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601392"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR Sharing 240: Più dispositivi HoloLens

Ologrammi vengono specificati sulla presenza nel mondo tramite rimanenti posto col passaggio nello spazio. HoloLens mantiene vntana posto utilizzando vari [sistemi di coordinate](coordinate-systems.md) per tenere traccia della posizione e l'orientamento di oggetti. Quando si condividono questi sistemi di coordinate tra i dispositivi, è possibile creare un'esperienza condivisa che consente di partecipare a un mondo holographic condiviso.

In questa esercitazione si apprenderà come:

* Configurare una rete per un'esperienza condivisa.
* Condividere vntana tra dispositivi HoloLens.
* Informazioni su altri utenti nel mondo holographic condiviso.
* È possibile creare un'esperienza interattiva condivisa in cui è possibile gli altri giocatori - di destinazione e avviare i proiettili a tali file.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR Sharing 240: Più dispositivi HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md) con accesso a Internet.
* Almeno due dispositivi HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso. Mantenere il nome di cartella **SharedHolograms**.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capitolo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In questo capitolo verranno configurare il primo progetto Unity e procedere con la compilazione e processo di distribuzione.

### <a name="objectives"></a>Obiettivi

* Configurare Unity per lo sviluppo di App holographic.
* Scopri le ologrammi!

### <a name="instructions"></a>Istruzioni

* Avviare Unity.
* Selezionare **aperto**.
* Immettere il percorso come il **SharedHolograms** cartella precedentemente non archiviati.
* Selezionare **nome progetto** e fare clic su **Seleziona cartella**.
* Nel **gerarchia**, fare doppio clic il **Main Camera** e selezionare **Elimina**.
* Nel **HoloToolkit-Sharing-240/Prefabs/fotocamera** cartella trovare il **Main Camera** prefab.
* Trascinare e rilasciare il **Main Camera** nel **gerarchia**.
* Nel **gerarchia**, fare clic su **Create** e **Crea vuoto**.
* Fare doppio clic su nuova **GameObject** e selezionare **rinominare**.
* Rinominare gli elementi GameObject al **HologramCollection**.
* Selezionare il **HologramCollection** dell'oggetto nel **gerarchia**.
* Nel **Inspector** impostare il **trasformare posizione** per: **X: 0, Y: -0,25, Z: 2**.
* Nel **Vntana** cartella la **pannello progetto**, trovare il **EnergyHub** asset.
* Trascinare e rilasciare il **EnergyHub** dell'oggetto dal **pannello progetto** per il **gerarchia** come un **figlio HologramCollection**.
* Selezionare **File > Salva scena come...**
* Denominare la scena **SharedHolograms** e fare clic su **salvare**.
* Premere il **riprodurre** pulsante in Unity per visualizzare in anteprima il vntana.
* Premere **riprodurre** una seconda volta per arrestare la modalità di anteprima.

**Esporta il progetto di Unity a Visual Studio**
* Nella finestra Seleziona Unity **File > Build Settings**.
* Fare clic su **aggiungere scene Open** per aggiungere la scena.
* Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.
* Impostare **SDK** al **10 universale**.
* Impostare **dispositivo di destinazione** al **HoloLens** e **tipo di compilazione UWP** al **D3D**.
* Controllare **Unity C# progetti**.
* Fai clic su **Compila**.
* Nella finestra di Esplora file che viene visualizzato, creare un **nuova cartella** denominato "App".
* Solo clic i **App** cartella.
* Premere **Seleziona cartella**.
* Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.
* Aprire il **App** cartella.
* Aprire **SharedHolograms.sln** per avviare Visual Studio.
* Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X86**.
* Fare clic sulla freccia giù accanto al computer locale e selezionare **dispositivo remoto**.
    * Impostare il **indirizzo** al nome o indirizzo IP di HoloLens. Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate** o chiedere a Cortana **"Ehi Cortana, qual è l'indirizzo IP?"**
    * Lasciare il **modalità di autenticazione** impostata su **universale**.
    * Fare clic su **selezionare**
* Fare clic su **Debug > Avvia senza eseguire debug** o premere **Ctrl + F5**. Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Inserire nella finestra di HoloLens e trovare l'ologrammi EnergyHub.

## <a name="chapter-2---interaction"></a>Capitolo 2: interazione

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In questo capitolo, è possibile interagire con i nostri vntana. In primo luogo, si aggiungerà un cursore da visualizzare nostri [estasiati](gaze.md). Quindi, aggiungiamo [movimenti](gestures.md) e utilizzare la mano per inserire i nostri vntana nello spazio.

### <a name="objectives"></a>Obiettivi

* Usare sguardo di input per controllare un cursore.
* Usare i movimenti di input per interagire con vntana.

### <a name="instructions"></a>Istruzioni

**Sguardo**
* Nel **Pannello di gerarchia** selezionare la **HologramCollection** oggetto.
* Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.
* Nel menu, digitare nella casella di ricerca **estasiati Manager**. Selezionare il risultato della ricerca.
* Nel **240\Prefabs\Input condivisione HoloToolkit** cartella trovare il **cursore** asset.
* Trascinare e rilasciare il **cursore** asset nel **gerarchia**.

**Movimento**
* Nel **Pannello di gerarchia** selezionare la **HologramCollection** oggetto.
* Fare clic su **Add Component** e digitare **movimento Manager** nel campo di ricerca. Selezionare il risultato della ricerca.
* Nel **Pannello di gerarchia**, espandere **HologramCollection**.
* Selezionare l'elemento figlio **EnergyHub** oggetto.
* Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.
* Nel menu, digitare nella casella di ricerca **posizionamento ologrammi**. Selezionare il risultato della ricerca.
* Salvare la scena selezionando **File > Salva scena**.

**Distribuire e sfrutta i vantaggi**
* Compilare e distribuire il HoloLens, seguendo le istruzioni riportate nel capitolo precedente.
* Una volta che l'app viene avviata nella finestra di HoloLens, spostarsi all'interno di head e notare il modo in cui il EnergyHub segue lo sguardo.
* Si noti come il cursore visualizzato quando estasiati al momento di ologramma e passa a una luce puntiforme quando non gazing in ologramma.
* Eseguire un puntato per posizionare l'ologramma. In questo momento nel progetto, è possibile inserire solo una volta l'ologrammi (ridistribuzione per riprovare).

## <a name="chapter-3---shared-coordinates"></a>Capitolo 3 - condiviso coordina

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Per visualizzare e interagire con vntana divertente, ma è possibile andare oltre. Verrà configurato il primo condividere esperienze - ologramma tutti possono visualizzare insieme.

### <a name="objectives"></a>Obiettivi

* Configurare una rete per un'esperienza condivisa.
* Stabilire un punto di riferimento comuni.
* Condividi i sistemi di coordinate tra i dispositivi.
* Tutti visualizzino lo stesso ologrammi!

>[!NOTE]
>Il **InternetClientServer** e **PrivateNetworkClientServer** funzionalità devono essere dichiarate per un'app per la connessione al server di condivisione. Questa operazione viene eseguita per è già in 240 Vntana, ma tenere a mente per i propri progetti.
>1. Nell'Editor di Unity, passare alle impostazioni del giocatore, passare a "Modifica > progetto Impostazioni > Player"
>2. Fare clic sulla scheda "Windows Store"
>3. Nella sezione "Impostazioni > le funzionalità di pubblicazione", controllare la **InternetClientServer** funzionalità e i **PrivateNetworkClientServer** funzionalità

### <a name="instructions"></a>Istruzioni

* Nel **pannello progetto** passare alle **240\Prefabs\Sharing condivisione HoloToolkit** cartella.
* Trascinare e rilasciare il **Sharing** prefab nel **Pannello di gerarchia**.

Successivamente è necessario avviare il servizio di condivisione. Solo **un PC** esperienza condiviso dovrà eseguire questo passaggio.
* In Unity - nel menu superiore-a - selezionare il **dal menu di 240 condivisione HoloToolkit**.
* Selezionare il **Avvia servizio di condivisione** elemento nell'elenco a discesa.
* Controllare la **Private Network** opzione e fare clic su **consentire l'accesso** quando la richiesta di firewall viene visualizzata.
* Annotare l'indirizzo IPv4 visualizzato nella finestra della console del servizio di condivisione. Questo è lo stesso indirizzo IP come il servizio è in esecuzione nel computer.

Seguire le istruzioni **tutti i PC** che verranno aggiunte le esperienze condivise.
* Nel **gerarchia**, selezionare la **Sharing** oggetto.
* Nel **Inspector**via la **Sharing fase** componente, modifica il **indirizzo del Server** da 'localhost' per l'indirizzo IPv4 del computer che esegue SharingService.exe.
* Nel **gerarchia** selezionare la **HologramCollection** oggetto.
* Nel **Inspector** fare clic sui **Add Component** pulsante.
* Nella casella di ricerca, digitare **importazione esportazione ancoraggio Manager**. Selezionare il risultato della ricerca.
* Nel **pannello progetto** passare alle **script** cartella.
* Fare doppio clic il **HologramPlacement** script per aprirlo in Visual Studio.
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

* In Unity, selezionare la **HologramCollection** nel **Pannello di gerarchia**.
* Nel **Pannello di controllo** fare clic sui **Add Component** pulsante.
* Nel menu, digitare nella casella di ricerca **App State Manager**. Selezionare il risultato della ricerca.

**Distribuire e sfrutta i vantaggi**
* Compilare il progetto per i dispositivi HoloLens.
* Designare uno HoloLens distribuire per prima. Sarà necessario attendere l'ancoraggio da caricare nel servizio prima di poter effettuare la EnergyHub (questa operazione può richiedere circa 30 e 60 secondi). Fino al completamento del caricamento, verranno ignorati i movimenti di tocco.
* Dopo aver posizionato il EnergyHub, posizione verrà caricata nel servizio e quindi è possibile distribuire a tutti gli altri dispositivi HoloLens.
* Quando si aggiunge un nuovo HoloLens prima di tutto la sessione, il percorso del EnergyHub potrebbe non essere corretto in tale dispositivo. Tuttavia, non appena l'ancoraggio e percorsi EnergyHub sono stati scaricati dal servizio, il EnergyHub deve spostarsi in corrispondenza per la nuova posizione condivisa. Se ciò non avviene entro circa 30 e 60 secondi, illustrato a dove il HoloLens originale era quando si imposta l'ancoraggio per raccogliere ulteriori indizi di ambiente. Se il percorso non blocca, ridistribuire il dispositivo.
* Quando i dispositivi sono pronti e che esegue l'app, cercare il EnergyHub. Di tutti concordare la posizione del ologrammi e direzione in cui è rivolta verso il testo?

## <a name="chapter-4---discovery"></a>Capitolo 4 - individuazione

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Tutti possono visualizzare ora lo stesso ologrammi! Ora vediamo come everyone else connesso al nostro mondo holographic condiviso. In questo capitolo, si sarà Ottiene la posizione head e la rotazione di tutti gli altri dispositivi HoloLens nella stessa sessione di condivisione.

### <a name="objectives"></a>Obiettivi

* Nella nostra esperienza condiviso individuarsi a vicenda.
* Scegliere e condividere un avatar Windows Media player.
* Collegare l'avatar player accanto teste di tutti.

### <a name="instructions"></a>Istruzioni

* Nel **pannello progetto** passare per il **Vntana** cartella.
* Trascinare e rilasciare il **PlayerAvatarStore** nel **gerarchia**.
* Nel **pannello progetto** passare alle **script** cartella.
* Fare doppio clic il **AvatarSelector** script per aprirlo in Visual Studio.
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

* Nel **gerarchia** selezionare la **HologramCollection** oggetto.
* Nel **Inspector** fare clic su **Add Component**.
* Nella casella di ricerca, digitare **gestione di Windows Media Player locale**. Selezionare il risultato della ricerca.
* Nel **gerarchia** selezionare la **HologramCollection** oggetto.
* Nel **Inspector** fare clic su **Add Component**.
* Nella casella di ricerca, digitare **gestione remota Windows Media Player**. Selezionare il risultato della ricerca.
* Aprire il **HologramPlacement** script in Visual Studio.
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

* Aprire il **AppStateManager** script in Visual Studio.
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

**Distribuire e sfrutta i vantaggi**
* Compilare e distribuire il progetto per i dispositivi HoloLens.
* Quando si sente un suono ping, individuare il menu di selezione avatar e selezionare un avatar con il movimento indice puntato.
* Se si osservano non qualsiasi vntana, il punto luce tutto il cursore attiverà un colore diverso quando comunica con il servizio di HoloLens: l'inizializzazione (viola scuro), scaricando il punto di ancoraggio (verde), l'importazione/esportazione di dati sulla località (giallo), caricare il punto di ancoraggio (blu). Se il punto luce tutto il cursore è il colore predefinito (viola chiaro), è pronti per interagire con gli altri giocatori nella sessione corrente.
* Esaminare altre persone connesse nello spazio - saranno presenti un robot holographic mobile sopra la spalla e, che rispecchia i movimenti head!

## <a name="chapter-5---placement"></a>Capitolo 5 - selezione host

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In questo capitolo, ci assicureremo di ancoraggio in grado di essere inseriti nelle aree del mondo reale. Useremo le coordinate condivise al posto che definiscono il punto medio tra tutti gli utenti connessi a condividere esperienze.

### <a name="objectives"></a>Obiettivi

* Inserire vntana sulla mappa spaziale in base alla posizione head giocatori.

### <a name="instructions"></a>Istruzioni

* Nel **pannello progetto** passare per il **Vntana** cartella.
* Trascinare e rilasciare il **CustomSpatialMapping** prefab nel **gerarchia**.
* Nel **pannello progetto** passare alle **script** cartella.
* Fare doppio clic il **AppStateManager** script per aprirlo in Visual Studio.
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

* Nel **pannello progetto** passare alle **script** cartella.
* Fare doppio clic il **HologramPlacement** script per aprirlo in Visual Studio.
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

**Distribuire e sfrutta i vantaggi**
* Compilare e distribuire il progetto per i dispositivi HoloLens.
* Quando l'app è pronta, in un cerchio in evidenza e notare come il EnergyHub viene visualizzato al centro di tutti gli utenti.
* Toccare per posizionare il EnergyHub.
* Provare il comando vocale 'Reimposta Target' per prelevare il EnergyHub il backup e lavorare insieme come gruppo per spostare l'ologrammi in una nuova posizione.

## <a name="chapter-6---real-world-physics"></a>Capitolo 6 - fisica reali

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In questo capitolo verrà aggiunto vntana che rimbalzano aree del mondo reale. Guarda lo spazio riempito di progetti avviati dall'utente e i tuoi amici.

### <a name="objectives"></a>Obiettivi

* Avviare i proiettili che rimbalzano aree del mondo reale.
* Condividere i proiettili in modo che gli altri giocatori possono visualizzarli.

### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** selezionare la **HologramCollection** oggetto.
* Nel **Inspector** fare clic su **Add Component**.
* Nella casella di ricerca, digitare **utilità di avvio proiettile**. Selezionare il risultato della ricerca.

**Distribuire e sfrutta i vantaggi**
* Compilare e distribuire ai dispositivi HoloLens.
* Quando l'app è in esecuzione in tutti i dispositivi, eseguire un puntato per avviare proiettile in superfici reali.
* Che cosa accade quando il proiettile è in conflitto con avatar del giocatore.

## <a name="chapter-7---grand-finale"></a>Capitolo 7 - gran

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In questo capitolo, si sarà scoprire un portale che può essere individuato solamente con la collaborazione.

### <a name="objectives"></a>Obiettivi

* Collaborano per avviare sufficiente i proiettili nel punto di ancoraggio per individuare un portale del segreto.

### <a name="instructions"></a>Istruzioni

* Nel **pannello progetto** passare per il **Vntana** cartella.
* Trascinare e rilasciare il **Underworld** asset come una **figlio HologramCollection**.
* Con **HologramCollection** selezionata, fare clic il **Add Component** pulsante il **Inspector**.
* Nel menu, digitare nella casella di ricerca **ExplodeTarget**. Selezionare il risultato della ricerca.
* Con **HologramCollection** selezionato, dalle **gerarchia** trascinare il **EnergyHub** dell'oggetto per il **destinazione** campo il **Inspector**.
* Con **HologramCollection** selezionato, dalle **gerarchia** trascinare il **Underworld** dell'oggetto per il **Underworld** campo il  **Inspector**.

**Distribuire e sfrutta i vantaggi**
* Compilare e distribuire ai dispositivi HoloLens.
* Quando l'app è stata avviata, collaborare per avviare i proiettili nel EnergyHub.
* Quando viene visualizzata la underworld, avviare i proiettili a controllare i robot underworld (riscontri un robot tre volte per divertimento extra).
