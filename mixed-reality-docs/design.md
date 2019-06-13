---
layout: LandingPage
title: Progettazione
description: Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP). Si tratta di un set di argomenti utili per la progettazione di app Windows per caschi con visore.
author: rwinj
ms.author: randyw
ms.date: 03/21/2018
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, progettazione, interazione, stile, colore, modelli di app, controlli, app di esempio, Mixed Reality Toolkit, MRTK
ms.openlocfilehash: 88de9008dbea6cce3b980bbbe3d0f45b7818e7c9
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66039205"
---
# <a name="design-for-mixed-reality"></a>Progettazione per la realtà mista

![Progettazione per la realtà mista](images/Bicycle-Leschi10.gif)

Queste linee guida sono state create da progettisti, sviluppatori, program manager e ricercatori Microsoft impegnati nella realizzazione di dispositivi olografici (come HoloLens) e dispositivi di tipo immersive (come i visori VR di Windows Mixed Reality Acer e HP). Si tratta di un set di argomenti utili per la progettazione di app Windows per caschi con visore.

## <a name="article-categories"></a>Categorie di articoli

<ul class="panelContent cardsF">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/GetStartedIcon.png" alt="Getting started icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introduzione alla progettazione</h3>
                        <p>
                            <a href="mixed-reality.md">Che cos'è la realtà mista?</a>
                        </p>
                        <p>
                            <a href="about-this-design-guidance.md">Informazioni su queste linee guida per la progettazione</a>
                        </p>
                        <p>
                            <a href="case-study-my-first-year-on-the-hololens-design-team.md">Il mio primo anno nel team di progettazione</a>
                        </p>
                        <p>
                            <a href="case-study-expanding-the-design-process-for-mixed-reality.md">Espansione del processo di progettazione per la realtà mista</a>
                        </p>
                        <p>
                            <a href="case-study-the-pursuit-of-more-personal-computing.md">La ricerca di un'esperienza di uso del computer più personale</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Interaction_Icon_120x130.png" alt="MR design system and tools icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Sistema e strumenti di progettazione per la realtà mista</h3>
                        <p>
                            <a href="comfort.md">Comodità</a>
                        </p>
            <p>
                            <a href="interaction-fundamentals.md">Interazioni istintive</a>
                        </p>
                        <p>
                            <a href="hands-and-tools.md">Mani e controller del movimento</a>
                        </p>
                        <p>
                            <a href="hands-free.md">Mani libere</a>
                        </p>
                         <p>
                            <a href="gaze-and-commit.md">Puntamento con la testa e commit</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Style_Icon_120x130.png" alt="Style icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Stile</h3>
                        <p>
                            <a href="color,-light-and-materials.md">Colore, chiaro e materiali</a>
                        </p>
                         <p>
                            <a href="spatial-sound-design.md">Progettazione dell'audio spaziale</a>
                        </p>
                        <p>
                            <a href="typography.md">Tipografia</a>
                        </p>
                        <p>
                            <a href="scale.md">Ridimensionamento</a>
                        </p>                      
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/App_patterns_Icon_120x130.png" alt="App patterns icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Modelli di app</h3>
                        <p>
                            <a href="types-of-mixed-reality-apps.md">Tipi di app di realtà mista</a>
                        </p>
                        <p>
                            <a href="room-scan-visualization.md">Visualizzazione della scansione dello spazio</a>
                        </p>
                        <p>
                            <a href="cursors.md">Cursori</a>
                        </p>
                        <p>
                            <a href="billboarding-and-tag-along.md">Billboarding e tag-along</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Controls_Icon_120x130.png" alt="Controls icon">
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Controlli</h3>
                        <p>
                            <a href="text-in-unity.md">Testo in Unity</a>
                        </p>
                        <p>
                            <a href="interactable-object.md">Oggetto con supporto per interazioni</a>
                        </p>
                        <p>
                            <a href="object-collection.md">Raccolta di oggetti</a>
                        </p>
                        <p>
                            <a href="progress.md">Visualizzazione dello stato</a>
                        </p>
                        <p>
                            <a href="app-bar-and-bounding-box.md">Barra dell'app e cubo di delimitazione</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </li>    
</ul>


## <a name="sample-apps"></a>App di esempio

Crea esperienze di alto livello a partire dagli esempi progettati e creati dal nostro team.

<br>
<ul id="cardtypes-W" class="cardsW panelContent" style="display: flex; margin-top: 0px;">
    <li>
        <a href="periodic-table-of-the-elements.md" title="Tavola periodica degli elementi" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/periodictableofelementsapp-tile.jpg" alt="Periodic Table of the Elements< icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>Tavola periodica degli elementi</h3>
                            <p>Informazioni su come definire il layout di una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti.</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>        
    </li>
    <li>
        <a href="lunar-module.md" title="Modulo lunare" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/lunar-module-tile.png" alt="Lunar Module icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>Modulo lunare</h3>
                            <p>Informazioni su come estendere i movimenti di base di HoloLens con tracciamento a due mani e input del controller Xbox.</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li>
        <a href="galaxy-explorer.md" title="Galaxy Explorer" data-linktype="absolute-path">
            <div class="cardSize">
                <div class="cardPadding">
                    <div class="card">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img src="images/galaxyexplorer-tile.jpg" alt="Galaxy Explorer icon">
                            </div>
                        </div>
                        <div class="cardText">
                            <h3>Galaxy Explorer</h3>
                            <p>Il progetto Galaxy Explorer è pronto. Hai condiviso le tue idee con la community, hai scelto un'app, hai osservato un team durante la fase di sviluppo e ora puoi avere il codice sorgente.</p>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>



## <a name="design-tools"></a>Strumenti di progettazione


<ul id="cardtypes-D" class="cardsD panelContent" style="display: flex; margin-top: 0px;">
    <li>
    <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" title="Mixed Reality Toolkit - Unity" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/MRTKandUnity.png" alt="Mixed Reality Toolkit - Unity">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Mixed Reality Toolkit - Unity</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
    <li>
    <a href="https://github.com/Microsoft/MixedRealityToolkit" title="Mixed Reality Toolkit" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/MRTK.png" alt="Mixed Reality Toolkit">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Mixed Reality Toolkit</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
        <li>
    <a href="case-study-building-holosketch,-a-spatial-layout-and-ux-sketching-app-for-hololens.md" title="HoloSketch" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/HoloSketch.png" alt="HoloSketch">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>HoloSketch</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
            <li>
    <a href="https://www.simplygon.com" title="Simplygon" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Simplygon.png" alt="Simplygon">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Simplygon</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
</ul>


## <a name="general-design-resources"></a>Risorse di progettazione generali

<ul id="cardtypes-D" class="cardsD panelContent" style="display: flex; margin-top: 0px;">
    <li>
    <a href="http://fluent.microsoft.com" title="Sistema di progettazione Fluent Design" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Fluent.png" alt="Fluent Design System">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Sistema di progettazione Fluent Design</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>
    <li>
    <a href="https://www.microsoft.com/design/inclusive" title="Progettazione inclusiva di Microsoft" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/Inclusive.png" alt="Inclusive design at Microsoft">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Progettazione inclusiva di Microsoft</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
        <li>
    <a href="https://developer.microsoft.com/windows/apps/design" title="Progettazione di app UWP (Universal Windows Platform)" data-linktype="absolute-path">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="images/UWP.png" alt="Universal Windows Platform (UWP) app design">
                        </div>
                    </div>                    
            <div class="cardText">
                        <h3>Progettazione di app UWP (Universal Windows Platform)</h3>
                        <p> </p>
                    </div>
                </div>
            </div>
        </div>
      </a>  
    </li>   
</ul>
