---
title: Colore, luce e materiali
description: La progettazione di contenuto per la realtà mista richiede un'attenta considerazione di colore, illuminazione e materiali per ognuno degli asset visivi usati nell'esperienza utente.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, colore, luce, materiali
ms.openlocfilehash: bef0c8b63c109baa536e4192ce94919eb888faf2
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896513"
---
# <a name="color-light-and-materials"></a>Colore, luce e materiali

La progettazione di contenuto per la realtà mista richiede un'attenta considerazione di colore, illuminazione e materiali per ognuno degli asset visivi usati nell'esperienza utente. Queste decisioni possono essere per entrambi gli scopi estetici, ad esempio l'uso di luce e materiale per impostare il tono di un ambiente immersivo e le finalità funzionali, ad esempio l'uso di colori sorprendenti per avvertire gli utenti di un'azione imminente. Ognuna di queste decisioni deve essere ponderata rispetto alle opportunità e ai vincoli del dispositivo di destinazione dell'esperienza.

Di seguito sono riportate le linee guida specifiche per il rendering degli asset su auricolari immersivi e olografici. Molti di questi elementi sono strettamente legati ad altre aree tecniche e un elenco di argomenti correlati è reperibile nella sezione [vedere anche](color,-light-and-materials.md#see-also) alla fine di questo articolo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering su dispositivi immersivi e olografici

Il contenuto di cui è stato eseguito il rendering negli auricolari immersivi viene visualizzato in modo visivo diverso rispetto al contenuto visualizzato negli auricolari olografici. Mentre gli auricolari immersivi in genere eseguono il rendering del contenuto in modo analogo a quanto ci si aspetterebbe in una schermata 2D, le cuffie olografiche come HoloLens usano le visualizzazioni RGB a colori sequenziali per il rendering degli ologrammi.

Per testare le esperienze olografiche in un auricolare olografico, è necessario sempre tempo. L'aspetto del contenuto, anche se è compilato in modo specifico per i dispositivi olografici, sarà diverso da quello dei monitoraggi secondari, degli snapshot e della visualizzazione spettatore. Ricordarsi di esaminare le esperienze con un dispositivo, testare l'illuminazione degli ologrammi e osservare tutti i lati (oltre a quanto sopra e sotto) come viene eseguito il rendering del contenuto. Assicurarsi di eseguire il test in un intervallo di impostazioni di luminosità sul dispositivo, in quanto è improbabile che tutti gli utenti condividano un valore predefinito presupposto, oltre a una serie diversificata di condizioni di illuminazione.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Nozioni fondamentali sul rendering nei dispositivi olografici
* I **dispositivi olografici hanno visualizzazioni additive** : gli ologrammi vengono creati aggiungendo luce alla luce dal mondo reale. il bianco verrà visualizzato con luminosità, mentre il nero verrà visualizzato come trasparente.
* **L'impatto sui colori varia a seconda dell'ambiente dell'utente. le** varie condizioni di illuminazione sono disponibili nella stanza di un utente. Consente di creare contenuti con livelli di contrasto appropriati per una maggiore chiarezza.
* **Evitare l'illuminazione dinamica** : gli ologrammi illuminati in modo uniforme nelle esperienze olografiche sono i più efficienti. L'uso di un'illuminazione dinamica avanzata può probabilmente superare le funzionalità dei dispositivi mobili. Quando è richiesta l'illuminazione dinamica, è consigliabile usare lo [shader di Mixed Reality Toolkit standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Progettazione con colore

A causa della natura delle visualizzazioni additive, alcuni colori possono apparire diversi in schermi olografici. Alcuni colori verranno visualizzati in ambienti di illuminazione mentre altri saranno meno interessati. I colori a freddo tendono a tornare in background, mentre i colori caldi vengono spostati in primo piano. Considerare questi fattori quando si esplorano i colori nelle proprie esperienze:
* **Gamut** -HoloLens trae vantaggio da una "ampia gamma di colori", concettualmente simile ad Adobe RGB. Di conseguenza, alcuni colori possono presentare diverse qualità e rappresentazione nel dispositivo.
* **Gamma** : la luminosità e il contrasto dell'immagine sottoposta a rendering variano tra i dispositivi immersivi e olografici. Queste differenze di dispositivi spesso sembrano creare aree scure di colore e ombreggiature, più o meno luminose.
* **Separazione** dei colori, nota anche come "interruzione del colore" o "frangia del colore", la separazione dei colori si verifica in genere con gli ologrammi mobili (incluso il cursore) quando un utente tiene traccia degli oggetti con gli occhi.
* Uniformità dei **colori** : in genere gli ologrammi vengono resi sufficientemente luminosi in modo da mantenere l'uniformità dei colori, indipendentemente dallo sfondo. È possibile che le aree grandi diventino macchie. Evitare grandi aree di colore chiaro e a tinta unita.
* Il **rendering di colori luminosi** . il bianco appare molto chiaro e deve essere usato con moderazione. Per la maggior parte dei casi, si consideri un valore bianco intorno a R 235 G 235 B 235. Le vaste aree luminose possono causare disagi da parte dell'utente.

**Rendering di colori scuri**

A causa della natura degli schermi additivi, i colori scuri appaiono trasparenti. Un oggetto nero a tinta unita non verrà visualizzato nel mondo reale. Vedere il canale alfa sotto. Per dare l'impressione di "nero", provare con un valore RGB grigio molto scuro, ad esempio 16, 16, 16.

![Gamma di colori normale rispetto a wide](images/640px-widegamut.png)<br>
*Gamma di colori normale rispetto a wide*

## <a name="technical-considerations"></a>Considerazioni tecniche
* **Aliasing** : si tratta di un aliasing, irregolare o "scale Steps", in cui il bordo della geometria di un ologramma soddisfa il mondo reale. L'uso di trame con un elevato livello di dettaglio può aggravare questo effetto. Le trame devono essere mappate e i filtri sono abilitati. Si consiglia di dissolvere i bordi degli ologrammi o di aggiungere una trama che crei un bordo nero attorno agli oggetti. Evitare la geometria sottile laddove possibile.
* **Canale alfa** : è necessario cancellare il canale alfa in modo da renderlo completamente trasparente per tutte le parti in cui non viene eseguito il rendering di un ologramma. Lasciando i lead alfa non definiti agli artefatti visivi quando si acquisiscono immagini/video dal dispositivo o con la visualizzazione spettatore.
* **Ammorbidimento della trama** : poiché la luce è additiva nelle visualizzazioni olografiche, è preferibile evitare grandi aree di colore chiaro e a tinta unita, perché spesso non producono l'effetto visivo desiderato.

## <a name="storytelling-with-light-and-color"></a>Storie con luce e colore

Luce e colore possono aiutare a far apparire gli ologrammi in modo più naturale nell'ambiente dell'utente, oltre a fornire materiale sussidiario e guida per l'utente. Per le esperienze olografiche, considerare questi fattori quando si esplorano l'illuminazione e il colore:
* **Vignettatura** : un effetto "vignette" per scurire i materiali può aiutare a concentrare l'attenzione dell'utente sul centro del campo di visualizzazione. Questo effetto scurisce il materiale dell'ologramma a un raggio dal vettore di sguardi dell'utente. Si noti che questa operazione è efficace anche quando l'utente Visualizza gli ologrammi da un angolo obliquo o uno sguardo.
* **Enfasi** : attirare l'attenzione sugli oggetti o sui punti di interazione differenziando colori, luminosità e illuminazione. Per informazioni più dettagliate sui metodi di illuminazione nella narrazione, vedere [pixel cinematografoy-un approccio di illuminazione per la grafica dei computer](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).

![Uso del colore per mostrare l'enfasi per gli elementi di Storytelling, mostrati qui in una scena da frammenti.](images/640px-fragments.jpg)<br>
*Uso del colore per mostrare l'enfasi per gli elementi di Storytelling, mostrati qui in una scena da [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*

## <a name="see-also"></a>Vedere anche
* [Separazione dei colori](hologram-stability.md#color-separation)
* [Ologrammi](hologram.md)
* [Microsoft Design Language-colore](https://www.microsoft.com/design/color)
* [Colore di piattaforma UWP (Universal Windows Platform)](https://docs.microsoft.com/windows/uwp/style/color)
