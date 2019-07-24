---
title: Case Study-compilazione di HoloSketch, un layout spaziale e un'app per lo sketch di UX per HoloLens
description: HoloSketch è un layout spaziale su dispositivo e uno strumento di schizzo UX per HoloLens per aiutare a creare esperienze olografiche.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realtà mista di Windows, sketching, app
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524372"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Case Study-compilazione di HoloSketch, un layout spaziale e un'app per lo sketch di UX per HoloLens

HoloSketch è un layout spaziale su dispositivo e uno strumento di schizzo UX per HoloLens per aiutare a creare esperienze olografiche. HoloSketch funziona con una tastiera e un mouse Bluetooth abbinati, nonché comandi di movimento e voce. Lo scopo di HoloSketch è fornire un semplice strumento di layout UX per la visualizzazione e l'iterazione rapide.

![HoloSketch: Un layout spaziale e un'app di sketch di UX per HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: layout spaziale e app di sketch di UX per HoloLens*

![Semplice strumento di layout UX per la visualizzazione e l'iterazione rapide.](images/holosketch-image-02.png)<br>
*Semplice strumento di layout UX per la visualizzazione e l'iterazione rapide*

## <a name="features"></a>Funzionalità

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitive per gli studi rapidi e la creazione di prototipi di scalabilità

![Uso di forme primitive](images/holosketch-primitives-giphy.gif)

Usare forme primitive per gli studi di massa rapida e la creazione di prototipi di scalabilità.

### <a name="import-objects-through-onedrive"></a>Importare oggetti tramite OneDrive

![importazione di oggetti](images/holosketch-importobjects-giphy.gif)

Importa le immagini PNG/JPG o gli oggetti FBX 3D (richiede la creazione di pacchetti in Unity) nello spazio di realtà misto attraverso OneDrive.

### <a name="manipulate-objects"></a>Modificare oggetti

![manipolazione di oggetti](images/manipulate-objects-640px.jpg)

Modificare gli oggetti (spostamento/rotazione/ridimensionamento) con una nota interfaccia oggetto 3D.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/tastiera, movimenti e comandi vocali

![supporta Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch supporta mouse/tastiera, movimenti e comandi vocali Bluetooth.

## <a name="background"></a>Sfondo

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importanza dell'esperienza di progettazione nel dispositivo

Quando si progetta un elemento per HoloLens, è importante sperimentare la progettazione nel dispositivo. Una delle principali difficoltà nella progettazione di app in realtà mista è che è difficile ottenere la scalabilità, la posizione e la profondità, soprattutto tramite gli schizzi 2D tradizionali.

### <a name="cost-of-2d-based-communication"></a>Costo della comunicazione basata su 2D

Per comunicare efficacemente flussi e scenari UX ad altri, una finestra di progettazione può dedicare molto tempo alla creazione di asset usando strumenti 2D tradizionali come Illustrator, Photoshop e PowerPoint. Queste progettazioni 2D richiedono spesso ulteriori sforzi per convertirle in 3D. Alcune idee vengono perse in questa conversione da 2D a 3D.

### <a name="complex-deployment-process"></a>Processo di distribuzione complesso

Poiché la realtà mista è una nuova area di disegno, comporta una grande quantità di iterazioni di progettazione e di prova ed errori per natura. Per le finestre di progettazione che non hanno familiarità con strumenti quali Unity e Visual Studio, non è facile inserire un elemento in HoloLens. In genere è necessario eseguire il processo seguente per visualizzare le immagini 2D/3D nel dispositivo. Si tratta di un grande ostacolo per i progettisti che scorrono rapidamente idee e scenari.

![Processo di distribuzione complesso](images/holosketch-image-03-1000px.png)<br>
*Processo di distribuzione*

### <a name="simplified-process-with-holosketch"></a>Processo semplificato con HoloSketch

Con HoloSketch è stato voluto semplificare questo processo senza coinvolgere gli strumenti di sviluppo e l'associazione del portale per i dispositivi. Con OneDrive, gli utenti possono inserire facilmente risorse 2D/3D in HoloLens.

![Processo semplificato con HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Processo semplificato con HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Incoraggiare le soluzioni e i Thinking di progettazione tridimensionali

Abbiamo pensato che questo strumento darebbe ai progettisti la possibilità di esplorare le soluzioni in uno spazio effettivamente tridimensionale e di non rimanere bloccati in 2D. Non è necessario considerare la creazione di uno sfondo 3D per la propria interfaccia utente, poiché lo sfondo è il mondo reale nel caso di Hololens. HoloSketch apre una soluzione che consente ai progettisti di esplorare facilmente la progettazione 3D in Hololens.

## <a name="get-started"></a>Introduzione

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Come importare immagini 2D (JPG/PNG) in HoloSketch

* Caricare le immagini JPG/PNG nella cartella OneDrive "Documents/HoloSketch".
* Dal menu OneDrive in HoloSketch sarà possibile selezionare e inserire l'immagine nell'ambiente.

![Importazione di immagini 2D](images/import-2d-images-1000px.jpg)<br>
*Importazione di immagini e oggetti 3D tramite OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Come importare oggetti 3D in HoloSketch

Prima di caricare nella cartella OneDrive, attenersi alla procedura seguente per creare un pacchetto degli oggetti 3D in un bundle di asset Unity. Con questo processo è possibile importare i file FBX/OBJ dal software 3D, ad esempio Maya, cinema 4D e Microsoft Paint 3D.

>[!IMPORTANT]
>Attualmente la creazione di bundle di asset è supportata con Unity Version 5.4.5 F1.

1. Scaricare e aprire il progetto Unity [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Questo progetto Unity include lo script per la generazione di asset bundle.
2. Creare un nuovo GameObject.
3. Denominare il GameObject in base al contenuto.
4. Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider '. 

   ![Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider '](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider ' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importare il file FBX 3D trascinandolo nel pannello del progetto.
6. Trascinare l'oggetto nel pannello gerarchia **sotto il nuovo GameObject**.

   ![Trascinare l'oggetto nel pannello gerarchia sotto il nuovo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Modificare la dimensione del Collider se non corrisponde all'oggetto. Ruotare l'oggetto sull' **asse Z**.

   ![Modificare la dimensione del Collider se non corrisponde all'oggetto.](images/holosketch-13-assetbundles-1000px.png)

8. Trascinare l'oggetto dal pannello gerarchia al pannello del progetto per **renderlo**prefabbricato.
9. Nella parte inferiore del pannello Inspector fare clic sull'elenco a discesa, creare e assegnare un nuovo nome univoco. Nell'esempio seguente viene illustrato come aggiungere e assegnare "brownchair" per il nome AssetBundle. 

   ![Nella parte inferiore del pannello Inspector fare clic sull'elenco a discesa e assegnare un nuovo nome univoco.](images/holosketch-14-assetbundles-1000px.png)

10. Preparare un'immagine di anteprima per l'oggetto modello. 
   ![Trascinare un'immagine nel pannello del progetto e assegnare il nome usato per l'oggetto.](images/holosketch-15-assetbundles-1000px.png)

11. Creare una cartella denominata "Assetbundles" nella cartella "asset" del progetto Unity.

12. Dal menu Asset selezionare ' compila AssetBundles ' per generare il file. 
   ![Dal menu Asset selezionare ' compila AssetBundles ' per generare il file.](images/holosketch-15a-assetbundles.png)


13. **Caricare il file generato nella cartella/Files/Documents/HoloSketch in OneDrive.** Caricare solo il file asset_unique_name. Non è necessario caricare file manifesto o file AssetBundles. <br>
![Aggiungere file a file/documenti/HoloSketch/cartella](images/holosketch-onedriveupload-1000px.png)
![. viene visualizzato un oggetto 3D aggiunto nel menu OneDrive di HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Come modificare gli oggetti

HoloSketch supporta l'interfaccia tradizionale ampiamente utilizzata nel software 3D. È possibile utilizzare Sposta, ruota, ridimensionare gli oggetti con movimenti e mouse. È possibile passare rapidamente da una modalità all'altra con la voce o la tastiera.

### <a name="object-manipulation-modes"></a>Modalità di manipolazione degli oggetti

![Come modificare gli oggetti](images/holosketch-image-06-1000px.png)<br>
*Come modificare gli oggetti*

### <a name="contextual-and-tool-belt-menus"></a>Menu contestuale e barra degli strumenti

**Uso del menu contestuale**

Toccare aria doppia per aprire il menu contestuale. 

Voci di menu:
* **Superficie layout:** Si tratta di un sistema Grid 3D in cui è possibile disporre più oggetti e gestirli come un gruppo. Toccare aria doppia sull'area del layout per aggiungere oggetti.
* **Primitives** Usare cubi, sfere, cilindri e coni per gli studi di massa.
* **OneDrive** Aprire il menu OneDrive per importare gli oggetti.
* **Guida:** Visualizza la schermata della guida.

![Menu contestuale](images/holosketch-image-07.png)<br>
*Menu contestuale*

**Uso del menu della barra degli strumenti**

Spostare, ruotare, ridimensionare, salvare e caricare la scena sono disponibili dal menu della barra degli strumenti. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Uso di tasti di scelta rapida, movimenti e comandi vocali

![Tastiera, movimenti e comandi vocali](images/holosketch-image-08-1000px.png)<br>
*Tastiera, movimenti e comandi vocali*

## <a name="download-the-app"></a>Scarica l'app

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Scaricare e installare gratuitamente l'app HoloSketch dalla Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemi noti
* La creazione del bundle di asset è attualmente supportata con **Unity Version 5.4.5 F1.**
* A seconda della quantità di dati nel OneDrive, l'app potrebbe apparire come se fosse stata arrestata durante il caricamento del contenuto di OneDrive
* Attualmente, la funzionalità Salva e carica supporta solo oggetti primitivi
* Menu di testo, audio, video e foto sono disabilitati nel menu contestuale
* Il pulsante Riproduci nel menu della barra degli strumenti Cancella i gizmo di manipolazione

## <a name="sharing-your-sketches"></a>Condivisione degli sketch

È possibile usare la funzionalità di registrazione video in HoloLens dicendo ' Hey Cortana, Start/Stop Registration '. Premere il tasto di scorrimento/discesa del volume per scattare un'immagine dello schizzo.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Progettazione UX@Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Sviluppatore@Microsoft</td>
</tr>
</table> 
