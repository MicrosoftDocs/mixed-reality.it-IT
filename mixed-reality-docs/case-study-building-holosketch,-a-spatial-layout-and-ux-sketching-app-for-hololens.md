---
title: 'Case study: Building HoloSketch, un layout spaziali e UX sketch di app per HoloLens'
description: HoloSketch è un layout spaziali sul dispositivo e dell'esperienza utente sketch strumento per HoloLens per la creazione di esperienze holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realtà mista di Windows, tracciare, app
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600133"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Case study: Building HoloSketch, un layout spaziali e UX sketch di app per HoloLens

HoloSketch è un layout spaziali sul dispositivo e dell'esperienza utente sketch strumento per HoloLens per la creazione di esperienze holographic. HoloSketch funziona con un comandi da tastiera e mouse, nonché gesti e voce Bluetooth abbinata. Lo scopo di HoloSketch è fornire uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione.

![HoloSketch: Un layout spaziali e UX sketch di app per HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout spaziali e UX sketch di app per HoloLens*

![Uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione.](images/holosketch-image-02.png)<br>
*Uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione*

## <a name="features"></a>Funzionalità

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitive per study rapido e scalabilità-creazione di prototipi

![Utilizzo delle forme primitive](images/holosketch-primitives-giphy.gif)

Usare le forme primitive per study massing rapido e scalabilità-creazione di prototipi.

### <a name="import-objects-through-onedrive"></a>Oggetti di importazione tramite OneDrive

![importazione di oggetti](images/holosketch-importobjects-giphy.gif)

Importare immagini PNG o JPG o oggetti FBX 3D (richiede la creazione di pacchetti in Unity) nello spazio di realtà mista tramite OneDrive.

### <a name="manipulate-objects"></a>Modificare gli oggetti

![la modifica degli oggetti](images/manipulate-objects-640px.jpg)

Modificare gli oggetti (spostamento/ruotare/scala) con un'interfaccia familiare oggetto 3D.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse e tastiera, movimenti e i comandi vocali

![supporta Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch supporta mouse e tastiera Bluetooth, movimenti e comandi vocali.

## <a name="background"></a>Informazioni

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importanza della verifica della progettazione del dispositivo

Quando si progetta qualcosa per HoloLens, è importante sperimentare la progettazione del dispositivo. Una delle principali sfide nella progettazione delle app di realtà mista è che è difficile ottenere il senso di scalabilità, posizione e profondità, in particolare nelle tradizionali schizzi 2D.

### <a name="cost-of-2d-based-communication"></a>Comunicazione basato sui costi di 2D

Per comunicare in modo efficace i flussi dell'esperienza utente e gli scenari ad altri utenti, una finestra di progettazione potrebbe avere un notevole dispendio di tempo di creazione di asset mediante gli strumenti tradizionali 2D, come Illustrator, Photoshop e PowerPoint. Questi progetti 2D spesso richiedono un impegno aggiuntivo per convertirli in 3D. Alcune informazioni vengono perse in questa conversione da 2D a 3D.

### <a name="complex-deployment-process"></a>Processo di distribuzione complesse

Poiché realtà mista è una nuova area di disegno per noi, comporta molti tentativi ed errori e iterazione di progettazione per sua natura. Finestra di progettazione che non hanno familiarità con gli strumenti, ad esempio Unity e Visual Studio, non è facile inserire un elemento tra loro in HoloLens. In genere è necessario seguire la procedura seguente per visualizzare la grafica 2D e 3D nel dispositivo. Si tratta di una barriera di big data per i progettisti rapidamente l'iterazione sugli scenari e le idee.

![Processo di distribuzione complesse](images/holosketch-image-03-1000px.png)<br>
*Processo di distribuzione*

### <a name="simplified-process-with-holosketch"></a>Processo semplificato con HoloSketch

Con HoloSketch, volevamo semplificare il processo senza coinvolgere gli strumenti di sviluppo e associazione del portale di dispositivo. Uso di OneDrive, gli utenti possono facilmente attivare gli asset 2D e 3D HoloLens.

![Processo semplificato con HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo semplificato con HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incoraggiando la mentalità progettazione tridimensionale e soluzioni

Abbiamo pensato di che questo strumento darebbe finestre di progettazione un'opportunità di Esplora soluzioni in uno spazio tridimensionale realmente e non essere bloccato in 2D. Non dovranno considerare creando un background 3D per l'interfaccia utente, poiché lo sfondo è di mondo reale in caso di Hololens. HoloSketch offre un modo per i progettisti di esplorare facilmente progettazione 3D in Hololens.

## <a name="get-started"></a>Introduzione

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Come importare immagini 2D JPG/PNG () in HoloSketch

* Caricare immagini JPG/PNG per la cartella di OneDrive ' Documenti/HoloSketch'.
* Dal menu di OneDrive nel HoloSketch, sarà possibile selezionare e copiare l'immagine nell'ambiente.

![L'importazione di immagini 2D](images/import-2d-images-1000px.jpg)<br>
*Importazione di immagini e oggetti 3D tramite OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Come importare oggetti 3D in HoloSketch

Prima di caricare la cartella di OneDrive, attenersi alla procedura seguente per creare un pacchetto di oggetti 3D in un bundle di asset di Unity. Utilizzo di questo processo è possibile importare i file FBX/OBJ da software 3D come Maya, Cinema 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Attualmente, la creazione di bundle di asset è supportata con Unity versione 5.4.5f1.

1. Scaricare e aprire il progetto di Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Questo progetto di Unity include lo script per la generazione di asset di bundle.
2. Creare un GameObject nuovo.
3. Denominare il GameObject basato sul contenuto.
4. Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider'. 

   ![Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importare il file FBX 3D trascinandolo nel Pannello di progetto.
6. Trascinare l'oggetto nel Pannello di gerarchia **sotto il nuovo GameObject**.

   ![Trascinare l'oggetto nel Pannello di gerarchia sotto il nuovo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Regolare la dimensione collider se non corrisponde l'oggetto. Ruotare l'oggetto per affrontare **asse z**.

   ![Regolare la dimensione collider se non corrisponde l'oggetto.](images/holosketch-13-assetbundles-1000px.png)

8. Trascinare l'oggetto dal Pannello di gerarchia al pannello di progetto per **renderlo prefab**.
9. Nella parte inferiore del Pannello di controllo, fare clic sul menu a discesa, creare e assegnare un nome univoco. Esempio seguente illustra l'aggiunta e l'assegnazione 'brownchair' per il nome AssetBundle. 

   ![Nella parte inferiore del Pannello di controllo, fare clic sul menu a discesa e assegnare un nuovo nome univoco.](images/holosketch-14-assetbundles-1000px.png)

10. Preparare un'immagine di anteprima per l'oggetto modello. 
   ![Trascinare un'immagine nel Pannello di progetto e assegnare il nome utilizzato per l'oggetto.](images/holosketch-15-assetbundles-1000px.png)

11. Creare una cartella denominata 'Assetbundles' nella cartella 'Asset' del progetto Unity.

12. Nel menu di asset, selezionare 'Build AssetBundles' per generare file. 
   ![Nel menu di asset, selezionare 'Build AssetBundles' per generare file.](images/holosketch-15a-assetbundles.png)


13. **Caricare il file generato nella cartella /Files/Documents/HoloSketch in OneDrive.** Caricare il file asset_unique_name solo. Non si dovranno caricare file AssetBundles o i file manifesto. <br>
![Aggiungere file al file/documenti/HoloSketch/cartella](images/holosketch-onedriveupload-1000px.png)
![verrà visualizzato un oggetto 3D aggiunto nel menu di OneDrive del HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Come modificare gli oggetti

HoloSketch supporta l'interfaccia tradizionali che è ampiamente usato in 3D software. È possibile utilizzare per spostare, ruotare, ridimensionare gli oggetti con i movimenti e un mouse. È possibile passare rapidamente tra modalità diverse con vocali o della tastiera.

### <a name="object-manipulation-modes"></a>Modalità di manipolazione di oggetti

![Come modificare gli oggetti](images/holosketch-image-06-1000px.png)<br>
*Come modificare gli oggetti*

### <a name="contextual-and-tool-belt-menus"></a>Menu contestuali e Tool Belt

**Tramite il menu di scelta rapida**

Indice puntato Double per aprire il menu di scelta rapida. 

Voci di menu:
* **Nell'area di layout:** Questo è un sistema di griglie 3D in cui è possibile modificare il layout più oggetti e gestirli come gruppo. Double-indice puntato nell'area di Layout per aggiungervi gli oggetti.
* **Primitive:** Usare i cubi, sfere, cilindri e coni per massing studi.
* **OneDrive:** Aprire il menu di OneDrive per importare gli oggetti.
* **aiuto:** Visualizza la Guida dello schermo.

![Menu di scelta rapida](images/holosketch-image-07.png)<br>
*Menu di scelta rapida*

**Usando il Menu di Tool Belt**

Spostare, ruota, scalabilità, salvataggio e caricamento scena sono disponibili dal Menu Tool Belt. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usando la tastiera, movimenti e comandi vocali

![Tastiera, movimenti e comandi vocali](images/holosketch-image-08-1000px.png)<br>
*Tastiera, movimenti e comandi vocali*

## <a name="download-the-app"></a>Scarica l'app

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Scaricare e installare l'app HoloSketch gratuitamente da di Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemi noti
* Attualmente è supportata la creazione di bundle di asset con **5.4.5f1 versione di Unity.**
* A seconda della quantità di dati in OneDrive, l'app potrebbe essere visualizzato come se è stato arrestato durante il caricamento del contenuto di OneDrive
* Attualmente, salvare e caricare oggetti primitivi supporta solo funzionalità
* Menu di testo, audio, Video e foto sono disabilitati nel menu di scelta rapida
* Il pulsante Play del menu Tool Belt Cancella il gizmo manipulation

## <a name="sharing-your-sketches"></a>Le bozze di condivisione

È possibile usare la funzionalità di registrazione video in HoloLens, pronunciare "Ehi Cortana, la registrazione di Start/Stop '. Premere il volume su/giù chiave insieme a scattare una foto dello sketch.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX Designer @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Per gli sviluppatori @Microsoft</td>
</tr>
</table> 
