---
title: Pacchetti MRTK
description: Questo articolo descrive i pacchetti che costituiscono il Toollkit di realtà mista di Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Realtà mista di Windows, MRTK, componente, pacchetto
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604640"
---
# <a name="mrtk-packages"></a>Pacchetti MRTK

Il Toolkit di realtà mista (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista cross-platform fornendo il supporto per l'hardware di realtà mista e piattaforme in modo strutturata in componenti.

Esistono tre categorie di pacchetti MRTK: 

* [Foundation](#foundation-packages)
* [Estensione](#extension-packages)
* [Sperimentale](#experimental-packages)

## <a name="foundation-packages"></a>Pacchetti di base

La base di Toolkit di realtà mista è il set di pacchetti che consentono all'applicazione di sfruttare le funzionalità comuni tra le piattaforme di realtà mista. Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) ramo in GitHub.

![Pacchetti Foundation MRTK](images/mrtk-foundation.jpg)

*Pacchetti Toolkit Foundation di realtà misti*

Le basi MRTK è costituita da:

* [Pacchetto di base](#core-package)
* [Provider di piattaforma](#platform-providers)
* [Servizi di sistema](#system-services)
* [Asset di funzionalità](#feature-assets)

Le sezioni seguenti descrivono i tipi di pacchetti in ogni categoria.

### <a name="core-package"></a>Pacchetto di base

Pacchetto di base è un _obbligatorio_ componente e viene eseguita come una dipendenza da tutti i pacchetti di foundation MRTK.

Il pacchetto MRTK Core include:

* [Tipi di interfacce, classi e dei dati comuni](#common-interfaces-clases-and-data-types)
* [Componente di scena MixedRealityToolkit](#mixedrealitytoolkit-scene-component)
* [MRTK Shader Standard](#mrtk-standard-shader)
* [Provider di Input di Unity](#unity-input-provider)
* [Gestione dei pacchetti](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>Tipi di interfacce, classi e dei dati comuni

Il pacchetto principale di Toolkit di realtà mista contiene le definizioni per tutte le interfacce comuni, le classi e tipi di dati usati da tutti gli altri componenti. Si consiglia vivamente che le applicazioni accedono componenti MRTK esclusivamente tramite le interfacce definite per garantire il massimo livello di compatibilità tra piattaforme.

#### <a name="mixedrealitytoolkit-scene-component"></a>Componente di scena MixedRealityToolkit

Il componente di scena MixedRealityToolkit è la gestione unica risorsa centralizzata per il Toolkit di realtà mista. Questo componente viene caricato e gestisce il ciclo di vita dei moduli di piattaforma e il servizio e vengono fornite risorse per i sistemi accedere alle relative impostazioni di configurazione. 

#### <a name="mrtk-standard-shader"></a>MRTK Shader Standard

Lo Shader Standard MRTK costituisce la base su quasi tutti i materiali forniti dal MRTK. Questo shader è estremamente flessibile e ottimizzato per la vasta gamma di piattaforme in cui MRTK è supportata. Si tratta _altamente_ consigliabile materiali dell'applicazione usano shader MRTK standard per ottenere prestazioni ottimali.

#### <a name="unity-input-provider"></a>Provider di Input di Unity

Il Provider di Input di Unity offre accesso ai dispositivi di input più comuni, ad esempio periferiche di gioco, touch screen e un mouse spaziale 3D.

#### <a name="package-management"></a>Gestione dei pacchetti

_Presto disponibili_

Pacchetto di base di Toolkit di realtà mista fornisce il supporto per l'individuazione e la gestione di foundation facoltativo, estensione e pacchetti MRTK sperimentale.

### <a name="platform-providers"></a>Provider di piattaforma

I pacchetti di Provider di piattaforma MRTK sono componenti che abilitano le funzionalità di piattaforma e il Toolkit di realtà mista alla destinazione dell'hardware di realtà mista.

Piattaforme supportate includono:

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Casella vocale di Windows](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Il pacchetto di realtà mista di Windows fornisce supporto per i dispositivi Microsoft HoloLens e coinvolgenti realtà mista di Windows. Il pacchetto contiene il supporto di intera piattaforma, tra cui:

* Sguardo targeting
* Movimenti
* Controller di movimento di realtà mista di Windows
* Mapping spaziale

#### <a name="openvr"></a>OpenVR

Il pacchetto OpenVR fornisce supporto per i dispositivi con la piattaforma OpenVR hardware e piattaforma.

#### <a name="windows-voice"></a>Casella vocale di Windows

Il pacchetto di casella vocale di Windows fornisce supporto per la funzionalità di riconoscimento dettatura e la parola chiave nei dispositivi Microsoft Windows 10.

### <a name="system-services"></a>Servizi di sistema

Servizi di piattaforma di base sono incluse nei pacchetti del servizio di sistema. Questi pacchetti contengono le implementazioni predefinite del Toolkit di realtà mista delle interfacce di servizio di sistema, definite nel [core](#core-package) pacchetto.

Le basi MRTK includono i servizi di sistema seguenti:

* [Sistema di limiti](#boundary-system)
* [Sistema di diagnostica](#diagnostic-system)
* [Sistema di input](#input-system)
* [Sistema di riconoscimento spaziali](#spatial-awareness-system)
* [Sistema teleport](#teleport-system)

#### <a name="boundary-system"></a>Sistema di limiti

Il sistema limiti MRTK fornisce dati relativi alla realtà virtuale a playspace. Nei sistemi per il quale l'utente ha configurato il limite, il sistema può fornire un piano floor, playspace rettangolare, area tracciata e altro ancora.

#### <a name="diagnostic-system"></a>Sistema di diagnostica

Il sistema di diagnostica MRTK fornisce i dati sulle prestazioni in tempo reale all'interno dell'esperienza dell'applicazione. In uso, sarà possibile visualizzare frequenza dei fotogrammi, il tempo del processore e altre metriche di prestazioni chiave quando si utilizza l'applicazione.

#### <a name="input-system"></a>Sistema di input

I sistemi di Input MRTK consente alle applicazioni di accedere all'input in modo cross-platform specificando le azioni degli utenti e assegnazione di tali azioni per i pulsanti più appropriati e degli assi nei controller di destinazione.

#### <a name="spatial-awareness-system"></a>Sistema di riconoscimento spaziali

Il sistema di riconoscimento spaziali MRTK consente l'accesso ai dati dell'ambiente reale da dispositivi, ad esempio il Microsoft HoloLens.

#### <a name="teleport-system"></a>Sistema teleport

Il sistema Teleport MRTK fornisce il supporto di realtà virtuale locomotion.

### <a name="feature-assets"></a>Asset di funzionalità

Gli asset di funzionalità sono raccolte di funzionalità correlate fornite come gli script e gli asset di Unity. Alcune di queste funzionalità includono:

* Controlli dell'interfaccia utente
* Risorse standard
* more

## <a name="extension-packages"></a>Pacchetti di estensione

I pacchetti di estensione MRTK sono una raccolta di pacchetti scritti da Microsoft e dalla Community che estendono e migliorano le funzionalità del Toolkit di realtà mista. Gli autori delle estensioni dello stato di tutte le dipendenze necessarie, contrassegna il pacchetto come compatibile con il Toolkit di realtà mista e fornire licenze e supportano le istruzioni.

I pacchetti di estensione possono fornire nuove funzionalità e supporto di nuove piattaforme. Nel corso del tempo, le estensioni possono, con l'assistenza e approvazione degli autori, eseguire la migrazione in base MRTK momento in cui verranno rilasciate e supportate da Microsoft.

![Pacchetto di estensione MRTK](images/mrtk-extensions.jpg)

*Pacchetti di estensione di Toolkit di realtà misti*

## <a name="experimental-packages"></a>Pacchetti sperimentale

I pacchetti sperimentale offrono la possibilità di funzionalità di prototipo dei voli, nelle versioni preliminari e nuove idee straordinarie. L'obiettivo di pacchetti più sperimentali è provare qualcosa di nuovo e per valutare l'interesse del cliente. Molte, anche se non tutti, pacchetti sperimentale sarà nuovamente rilasciati come estensioni del termine della creazione di prototipi e fase di test.

![Pacchetti sperimentale MRTK](images/mrtk-experimental.jpg)

*Pacchetti sperimentale Toolkit di realtà misti*

## <a name="conclusion"></a>Conclusione

I pacchetti di Toolkit di realtà mista e il sistema di gestione pacchetti sono progettati per consentire un metodo semplice e pulito per poter compilare modo additivo funzionalità nelle tue esperienze senza ricorrere a componenti non necessari da includere nel progetto.

Nel corso del tempo, verrà aggiunto il supporto di gestione pacchetti e migliorato nel Toolkit di realtà mista. Se si dispone di commenti e suggerimenti o si vuole ottenere coinvolti, visitare il [Toolkit di realtà mista progetto](https://github.com/Microsoft/MixedRealityToolkit-Unity) su GitHub. 

## <a name="see-also"></a>Vedere anche

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

