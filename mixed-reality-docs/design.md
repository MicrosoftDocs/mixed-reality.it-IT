---
layout: LandingPage
title: Iniziare a progettare e a creare prototipi
description: Se sei pronto per iniziare a creare, di seguito vengono illustrati i concetti di base che ti serviranno per iniziare a progettare e a creare prototipi.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, individuare, distribuire, indice, pagina di destinazione, progettazione, sviluppo, esercitazioni, app di esempio, nozioni di base, case study, risorse, guide pratiche per HoloLens, progetti open source, concetti di base, interazione
ms.openlocfilehash: 9ef408e1551e9f6c52a6c5fcf7df3123cc099c8c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334079"
---
# <a name="start-designing-and-prototyping"></a>Iniziare a progettare e a creare prototipi


![Progettazione astratta di realtà mista](images/03_Design.png)

## <a name="expand-your-design-processcase-study-expanding-the-design-process-for-mixed-realitymd"></a>[Espandere il processo di progettazione](case-study-expanding-the-design-process-for-mixed-reality.md)

Quando Microsoft lanciava HoloLens per un pubblico di sviluppatori entusiasti nel 2016, il team aveva già collaborato con studi all'interno e all'esterno di Microsoft per creare le esperienze di lancio del dispositivo. Questi team hanno imparato con la pratica, scoprendo sia le opportunità che le problematiche correlate al nuovo settore della progettazione per la realtà mista. [Altre informazioni](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>Quali sono i concetti di base di un'esperienza?

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[Fare in modo che l'utente possa operare comodamente (comfort)](comfort.md)
Per garantire il massimo comfort per i caschi con visore, è importante che i progettisti e gli sviluppatori creino e presentino contenuti in modo da simulare il funzionamento di questi segnali nel mondo naturale.

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[Considerare il modo in cui l'utente vede il mondo (frame olografico)](holographic-frame.md)
Gli utenti vedono il mondo della realtà mista attraverso un riquadro di visualizzazione rettangolare controllato tramite il visore VR. In HoloLens quest'area rettangolare è detta frame olografico e consente agli utenti di visualizzare il contenuto digitale sovrapposto al mondo reale circostante.

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[Tipi di app di realtà mista](types-of-mixed-reality-apps.md)
Uno dei vantaggi dello sviluppo di app di realtà mista è costituito dal fatto che la piattaforma può supportare un'ampia gamma di esperienze. Da ambienti virtuali completamente immersivi a una sovrapposizione poco invasiva di informazioni all'ambiente corrente di un utente, la realtà mista offre un set efficace di strumenti per creare qualsiasi tipo di esperienza.

<br>

### <a name="keeping-holograms-in-place---coordinate-systemscoordinate-systemsmd"></a>[Mantenere gli ologrammi nella posizione desiderata (sistemi di coordinate)](coordinate-systems.md)
Essenzialmente le app di realtà mista posizionano gli ologrammi nel tuo mondo in modo che abbiano l'aspetto di oggetti reali. Questo implica posizionare esattamente gli ologrammi in punti che siano significativi per l'utente, che si tratti di una stanza fisica o di un ambiente virtuale creato.

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[Far sembrare reali gli oggetti olografici (mapping spaziale)](spatial-mapping.md)
Il mapping spaziale consente di posizionare gli oggetti su superfici reali. In questo modo è possibile ancorare gli oggetti nel mondo dell'utente, sfruttando i segnali di profondità del mondo reale.

<br>


---

<br>

![Fattori di progettazione delle interazioni](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>Fattori di progettazione delle interazioni da considerare


### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[Scegliere un modello di interazione per il cliente](interaction-fundamentals.md)
La filosofia delle interazioni semplici e istintive è alla base di tutta la piattaforma Realtà mista. Abbiamo adottato tre accorgimenti per consentire ai progettisti e agli sviluppatori di applicazioni di fornire ai clienti interazioni facili e intuitive.

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[Mani e controller del movimento](hands-and-tools.md)
Gli utenti possono toccare e manipolare gli ologrammi direttamente con una o entrambe le mani come per gli oggetti reali. In alternativa, con i controller del movimento, puoi estendere le funzionalità fisiche dell'utente fornendo interazioni precise su un'ampia gamma di distanze.

<br>

### <a name="directly-commanding-objects-with-voice-inputvoice-inputmd"></a>[Gestire gli oggetti direttamente con l'input vocale](voice-input.md)
La voce è una delle forme di input chiave per HoloLens. Consente di gestire un ologramma direttamente senza dover usare i movimenti. L'input vocale può essere un modo naturale di comunicare le intenzioni.

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[Uso dello sguardo dell'utente](eye-tracking.md)
HoloLens 2 consente di raggiungere un nuovo livello di comprensione contestuale e umana all'interno dell'esperienza olografica, offrendo agli sviluppatori la possibilità di usare le informazioni relative a cosa gli utenti stanno guardando.

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[Colore, luce e materiali](color,-light-and-materials.md)
La progettazione di contenuto per la realtà mista richiede un'attenta considerazione del colore, dell'illuminazione e dei materiali per ognuno degli asset visivi usati nell'esperienza.

<br>

### <a name="suggesting-the-scale-of-an-objectscalemd"></a>[Suggerire la scala di un oggetto](scale.md)
Per visualizzare contenuto che sembri realistico in forma olografica, è importante simulare quanto più possibile le caratteristiche visive del mondo reale. Ciò significa incorporare il maggior numero possibile dei segnali visivi utili (nel mondo reale) per comprendere dove si trovino gli oggetti, quanto siano grandi e di cosa siano fatti.

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[Tipografia chiara e leggibile](typography.md)
Proprio come per la tipografia su schermi 2D, l'obiettivo è chiarezza e leggibilità. Grazie all'aspetto tridimensionale della realtà mista, è possibile influire sul testo e sull'esperienza utente complessiva in modo ancora più significativo.

<br>

### <a name="ux-elements-for-the-mixed-realityapp-patterns-landingpagemd"></a>[Elementi UX per la realtà mista](app-patterns-landingpage.md)
Scopri le caratteristiche dei componenti di base per le interazioni spaziali e l'interfaccia utente nella realtà mista.
<br>


---

## <a name="choose-a-prototyping-option"></a>Scegliere un'opzione per la creazione di prototipi  

:::row:::   
    :::column:::    
       [![Informazioni su Unity](images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Informazioni su Unity](https://learn.unity.com/)**<br>
        Scopri come creare esperienze interattive con Unity. Impara con la pratica, dall'inizio alla fine.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        Grazie all'interazione spaziale e ai componenti di base dell'interfaccia utente, puoi iniziare subito a progettare e sviluppare realtà miste con Unity.   
    :::column-end:::
    :::column:::    
        [![Laboratori di progettazione di realtà mista](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Laboratori di progettazione di realtà mista](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        Sono disponibili app di esempio che illustrano come usare i componenti di base del toolkit MRTK per creare esperienze di realtà mista accattivanti.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Progetta per la realtà mista. Microsoft Maquette consente di creare prototipi spaziali con un'esperienza semplice, rapida e immersiva. 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>Quali operazioni vuoi eseguire successivamente?

:::row:::
    :::column:::
       [![Acquisisci i concetti di base](images/icon-lightbulb.png)](index.md#understand-the-basics)<br>
        **[Acquisisci i concetti di base](index.md#understand-the-basics)**<br>
        Approfondisci il significato di realtà mista e come viene usata.
    :::column-end:::
    :::column:::
        [![Partecipa a un evento](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[Partecipa a un evento](sf-academy-events.md)**<br>
        Vieni a vedere l'hardware e partecipa all'esercitazione pratica per creare la tua prima applicazione HoloLens 2.
    :::column-end:::
    :::column:::
        [![Installa gli strumenti](images/icon-design.jpg)](install-the-tools.md)<br>
         **[Installa gli strumenti](install-the-tools.md)**<br>
        Usa l'elenco di controllo dell'installazione per ottenere gli strumenti necessari per creare app per HoloLens e per la realtà mista.
    :::column-end:::
    :::column:::
        [![Inizia a sviluppare](images/icon-developer.jpg)](development.md)<br>
        **[Inizia a sviluppare](development.md)**<br>
        Scegli un percorso di sviluppo in base al tuo livello di competenza, al tuo stile di lavoro o all'interesse per le piattaforme.
    :::column-end:::
:::row-end:::


<br>

<br>


