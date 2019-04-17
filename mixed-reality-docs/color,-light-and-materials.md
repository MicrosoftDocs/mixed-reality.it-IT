---
title: Colore, chiaro e materiali
description: Progettazione di contenuto per realtà mista richiede un'attenta valutazione del colore illuminazione e materiali per ogni asset visual utilizzato durante l'utilizzo.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, colore, luce, materiali
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601382"
---
# <a name="color-light-and-materials"></a>Colore, chiaro e materiali

Progettazione di contenuto per realtà mista richiede un'attenta valutazione del colore illuminazione e materiali per ogni asset visual utilizzato durante l'utilizzo. Tali decisioni possono essere per fini estetici, gradiscano chiaro e materiale per impostare il tono di un ambiente coinvolgente e concreto sia funzionali scopi, ad esempio utilizzando colori sorprendenti per avvisare gli utenti di un'azione imminente. Ognuna di queste decisioni deve essere confrontato con le opportunità e i vincoli dell'esperienza dispositivo di destinazione.

Di seguito sono linee guida specifiche per gli asset per il rendering in auricolari sia coinvolgenti e holographic. Molte di queste sono strettamente legati ad altre aree tecniche ed è disponibile un elenco di oggetti correlati nel [vedere anche](color,-light-and-materials.md#see-also) sezione alla fine di questo articolo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Eseguire il rendering sul coinvolgenti e holographic dispositivi

Il contenuto sottoposto a rendering in auricolari immersive apparirà visivamente diverso rispetto al contenuto sottoposto a rendering in auricolari holographic. Mentre cuffie coinvolgenti per il rendering del contenuto in genere così come si può immaginare sullo schermo 2D, holographic auricolari, ad esempio utilizzare HoloLens trasparente, in modo sequenziale colore RGB Visualizza vntana esegue il rendering.

Richiedere sempre possibile testare le proprie esperienze holographic in cuffie holographic. L'aspetto del contenuto, anche se viene compilato in modo specifico per i dispositivi holographic, sarà diversa come visto su monitora secondario, snapshot e nella visualizzazione spectator. Ricordarsi di camminare esperienze con un dispositivo, il test dell'illuminazione di ologrammi e osservando da tutti i lati (così come in precedenza e di sotto) la modalità di rendering del contenuto. Assicurarsi di testare una gamma di impostazioni luminosità del dispositivo, perché è improbabile che tutti gli utenti condivideranno un'impostazione predefinita, nonché un set eterogeneo di illuminazione.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Nozioni di base del rendering sui dispositivi holographic
* **Dispositivi holographic sono additivi Visualizza** – Vntana viene create aggiungendo più chiaro alla luce dal mondo reale: bianco apparirà vivace, durante il black verrà visualizzato come trasparente.
* **Impatto di colori varia con l'ambiente dell'utente** : sono presenti molte condizioni diverse illuminazione nella stanza dell'utente. Creare contenuti con livelli appropriati di contrasto elevato per facilitarne la comprensione.
* **Evitare di illuminazione dinamica** – Vntana che è illuminato in modo uniforme nelle esperienze di holographic risultano più efficienti. Con l'illuminazione avanzate e dinamiche supera in genere le funzionalità di shader per dispositivi mobili.

## <a name="designing-with-color"></a>Progettazione con colori

A causa della natura degli schermi additive, alcuni colori possono apparire diversi sulla visualizzazione olografiche. Alcuni colori verranno visualizzata negli ambienti di illuminazione, mentre gli altri verranno visualizzati come caso meno. I colori ad accesso sporadico tendono a spariscono in background mentre caldi passa in primo piano. Tenere presente questi fattori durante l'esplorazione di colore nelle proprie esperienze:
* **Gamma** -HoloLens trae vantaggio da una gamma"wide" di colore, concettualmente simile a Adobe RGB. Di conseguenza, alcuni colori possono presentare caratteristiche diverse e la rappresentazione nel dispositivo.
* **Gamma** -luminosità e contrasto dell'immagine visualizzata varia tra i dispositivi coinvolgenti e holographic. Queste differenze tra i dispositivi vengono visualizzati spesso per rendere le aree scure del colore e ombreggiature, più o meno brillanti.
* **La separazione dei colori** -noto anche come "suddivisione colore" o "colore la smarginatura", la separazione di colore si verifica in genere lo spostamento vntana (inclusi cursore) quando un utente tiene traccia degli oggetti con ai loro stessi occhi.
* **Colore dell'uniformità** -in genere vntana rendering viene eseguito abbastanza vivace in modo che mantengano uniformità di colore, indipendentemente dal fatto di background. Aree di grandi dimensioni possono diventare blotchy. Evitare le aree di grandi dimensioni del brillante, tinta unita.
* **Il rendering di colori chiari** -bianco visualizzato molto intensa e deve essere utilizzata con cautela. Per la maggior parte dei casi, è consigliabile un valore bianco intorno a R 235 G 235 B 235. Aree chiare elevate possono causare disturbo utente.

**Il rendering di colori scuri**

A causa della natura dell'addizione viene visualizzato, colori scuri appaiono trasparenti. Un oggetto di colore nero a tinta unita apparirà non differisce dal mondo reale. Canale alfa vedere riportato di seguito. Per assegnare l'aspetto di "black" provare un valore RGB di colore grigio scuro molto, ad esempio 16,16,16.

![Normale e ampia gamma di colori](images/640px-widegamut.png)<br>
*Normale e ampia gamma di colori*

## <a name="technical-considerations"></a>Considerazioni tecniche
* **Aliasing** -essere accurati di aliasing, irregolari o "scalini" in cui il bordo della geometria di ologramma soddisfi il mondo reale. Uso di trame con una visualizzazione dettagliata possa aggravare questo effetto. Devono essere mappate le trame e abilitato il filtro. Prendere in considerazione a dissolvenza i bordi del vntana o l'aggiunta di una trama che viene creato un bordo nero bordo attorno a oggetti. Evitare di geometria thin laddove possibile.
* **Canale alfa** -è necessario cancellare il canale alfa completamente trasparente per tutte le parti in cui non esegue il rendering ologramma. Lasciando i lead indefiniti alfa su elementi visivi quando si acquisisce le immagini o video dal dispositivo o con la visualizzazione Spectator.
* **Trama sfumare** : poiché è chiaro additivi in holographic consente di visualizzare, è consigliabile evitare le aree di grandi dimensioni del brillante, tinta unita come non producono spesso l'effetto desiderato.

## <a name="storytelling-with-light-and-color"></a>Condivisione di storie con chiaro e colori

Chiaro e colori facilitano la vntana vengono visualizzati in modo più naturale in di un utente ambiente, nonché forniscono indicazioni e Guida per gli utenti. Per le esperienze holographic, prendere in considerazione questi fattori durante l'esplorazione di colore e illuminazione:
* **Vignettatura** -un effetto 'vignette' viene resa più scura materiali consentono di concentrare l'attenzione dell'utente al centro del campo di visualizzazione. Questo effetto scurisce materiale di ologramma alcuni radius dal vettore sguardo dell'utente. Si noti che questo è valido anche quando l'utente visualizza vntana da un angolo colpisca o obliquo.
* **Enfasi** -attirare l'attenzione su oggetti o i punti di interazione per contrasto dei colori, luminosità e illuminazione. Per un'analisi più approfondita i metodi di illuminazione nella condivisione di storie, vedere [cinematografia Pixel - un approccio di illuminazione per infografica](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).

![Uso del colore per mostrare enfasi per gli elementi di condivisione di storie, illustrato di seguito in una scena da frammenti.](images/640px-fragments.jpg)<br>
*Uso del colore da visualizzare per gli elementi di condivisione di storie, illustrato di seguito in una scena di enfasi [frammenti](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*

## <a name="see-also"></a>Vedere anche
* [Separazione dei colori](hologram-stability.md#color-separation)
* [Ologrammi](hologram.md)
* [Language Design Microsoft - colore](https://www.microsoft.com/design/color)
* [(Universal Windows Platform)-colore](https://docs.microsoft.com/windows/uwp/style/color)
