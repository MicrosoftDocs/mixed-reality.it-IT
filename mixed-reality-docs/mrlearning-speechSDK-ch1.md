---
title: Esercitazioni su servizi vocali di Azure-1. Integrazione e utilizzo di riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: defa33e56cfe4450a8d42855bd11dc23973dc401
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913511"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. integrazione e utilizzo del riconoscimento vocale e della trascrizione

Questa esercitazione consente di creare un'applicazione di realtà mista che Esplora l'uso dell'SDK vocale di servizi cognitivi di Azure con HoloLens 2. Al termine di questa serie di esercitazioni, sarà possibile usare il microfono del dispositivo per trascrivere il riconoscimento vocale in un testo in tempo reale, tradurre il discorso in altre lingue e sfruttare la funzionalità Intent dell'SDK di riconoscimento vocale per comprendere i comandi vocali usando intelligenza artificiale.

## <a name="objectives"></a>Obiettivi

- Informazioni su come integrare Azure Speech SDK in un'applicazione HoloLens 2
- Informazioni su come usare i comandi vocali
- Informazioni su come usare le funzionalità di riconoscimento vocale

## <a name="instructions"></a>Istruzioni

### <a name="getting-started"></a>Attività iniziali

1. Avviare Unity e creare un nuovo progetto. Immettere il modulo di apprendimento del nome del progetto SDK. Scegliere un percorso in cui salvare il progetto. Fare quindi clic su Crea progetto.

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >Verificare che il modello sia impostato su 3D, come illustrato nell'immagine precedente.

2. Scaricare la versione del pacchetto di [reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [Foundation 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) e salvarla in una cartella del computer. Importare il pacchetto nel progetto Unity. Per istruzioni dettagliate su come eseguire questa operazione, vedere le [esercitazioni introduttive-lezione 2. Inizializzazione del progetto e della prima applicazione](mrlearning-base-ch1.md).

3. Scaricare e importare Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) per il pacchetto di asset di Unity. Importare il pacchetto di riconoscimento vocale facendo clic su asset, selezionare Importa pacchetto, quindi selezionare pacchetto personalizzato. Trovare il pacchetto SDK per la sintesi vocale scaricato in precedenza e aprirlo per avviare il processo di importazione.

    ![mrlearning-Speech-CH1-1-step3a. png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-Speech-CH1-1-step3b. png](images/mrlearning-speech-ch1-1-step3b.png)

4. Nella finestra popup successiva fare clic su Importa per avviare l'importazione del pacchetto di riconoscimento vocale. Verificare che tutti gli elementi siano controllati come illustrato nell'immagine seguente.

    ![mrlearning-Speech-CH1-1-step4. png](images/mrlearning-speech-ch1-1-step4.png)

5. Scaricare l'asset Pack del modulo Speech SDK, noto anche come pacchetto Lunarcom facendo clic su [questo collegamento](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2). Il pacchetto di asset Lunarcom è una raccolta di asset e script sviluppati per questa serie di lezioni che illustrano un uso pratico di Azure Speech SDK. Si tratta di un terminale del comando vocale che, infine, si interfaccia con l'esperienza degli assembly dei moduli lunari sviluppata nelle [esercitazioni introduttive-lezione 7. Creazione di un'applicazione di esempio Lunar Module](mrlearning-base-ch6.md).

6. Importare il pacchetto di asset Lunarcom nel progetto Unity seguendo una procedura analoga a quella impiegata per importare il Toolkit di realtà mista e l'SDK di riconoscimento vocale.

7. Configurare il Toolkit di realtà mista (MRTK).

    A tale scopo, fare clic sul pannello Toolkit realtà mista nella parte superiore della finestra e quindi selezionare Aggiungi a scena e configura.

    ![mrlearning-Speech-CH1-1-step7a. png](images/mrlearning-speech-ch1-1-step7a.png)

    Nella finestra popup visualizzata selezionare DefaultHoloLens2ConfigurationProfile per impostarlo come profilo attivo per il Toolkit di realtà mista.

    ![mrlearning-Speech-CH1-1-step7b. png](images/mrlearning-speech-ch1-1-step7b.png)

8. Nella scena sono ora presenti diversi nuovi elementi dal MRTK. Salvare la scena con un nome diverso facendo clic su "file", quindi su "Salva con nome" e denominare la scena SpeechScene.

    >[!NOTE]
    >Se si preme Riproduci sulla scena dopo aver aggiunto il MRTK al progetto e non si entra in modalità di riproduzione, potrebbe essere necessario riavviare Unity.

9. Con l'oggetto MixedRealityToolkit selezionato nella gerarchia della scena, fare clic su copia & Personalizza nel pannello di controllo per aprire il popup del profilo clone. Nella finestra popup profilo clone immettere un nome appropriato per il profilo personalizzato, ad esempio HoloLens2ConfigurationProfile personalizzato, quindi fare clic su Clona per creare il profilo di configurazione personalizzato e impostarlo come profilo attivo.

    ![mrlearning-Speech-CH1-1-step9. png](images/mrlearning-speech-ch1-1-step9.png)

10. Inoltre, nel pannello Inspector (con l'oggetto MixedRealityToolkit selezionato nella gerarchia) disabilitare il sistema di diagnostica deselezionando la casella a destra di Abilita sistema di diagnostica.

    ![mrlearning-Speech-CH1-1-Step10. png](images/mrlearning-speech-ch1-1-step10.png)

11. In questa esercitazione si usano i comandi di input vocale per il riconoscimento vocale e la trascrizione. Consente di clonare il profilo di input per apportare modifiche alle impostazioni vocali.

    Con l'oggetto MixedRealityToolkit ancora selezionato nella gerarchia della scena, fare clic sul pulsante Small clone nel pannello Inspector per aprire il popup del profilo clone. Nella finestra popup profilo clone immettere un nome appropriato per il profilo personalizzato, ad esempio HoloLens2InputSystemProfile personalizzato, quindi fare clic su Clona per creare il profilo di sistema di input personalizzato e impostarlo come profilo attivo.

    ![mrlearning-Speech-CH1-1-STEP11. png](images/mrlearning-speech-ch1-1-step11.png)

12. Una volta clonato il profilo di input, espandere la sezione Speech e seguire lo stesso processo del passaggio precedente per clonare il profilo dei comandi vocali.

    ![mrlearning-Speech-CH1-1-step12. png](images/mrlearning-speech-ch1-1-step12.png)

13. A questo punto, nella sezione sintesi vocale, passare a impostazioni generali e modificare il comportamento di avvio per iniziare manualmente.

    ![mrlearning-Speech-CH1-1-step13. png](images/mrlearning-speech-ch1-1-step13.png)

14. Nel pannello progetto espandere la cartella Lunarcom e trascinare il Lunarcom_Base prefabbricate nella gerarchia della scena.

    ![mrlearning-Speech-CH1-1-step14. png](images/mrlearning-speech-ch1-1-step14.png)

15. Selezionare l'oggetto Lunarcom_Base nella gerarchia e verificare che la posizione sia impostata su x = 0, y = 0 e z = 0, oltre che sulla rotazione impostata su x = 0, y = 0 e z = 0. Impostare la scala su Read x = 0.008, y = 0.008 e z = 0,01.

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Fare clic su Aggiungi componente e cercare e selezionare Lunarcom controller. Questo script è incluso nel pacchetto di risorse Lunarcom importato nel passaggio 6.

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Per connettere l'applicazione ai servizi cognitivi di Azure, è necessario immettere una chiave di sottoscrizione, nota anche come chiave API, per il servizio di riconoscimento vocale. Per ottenere una chiave di sottoscrizione gratuita, seguire le istruzioni riportate [qui](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) . Una volta ottenuta la chiave di sottoscrizione, immetterla nel campo chiave API del servizio vocale del componente LunarcomController nel pannello di controllo, come illustrato nell'immagine seguente.

18. Immettere l'area scelta al momento dell'iscrizione alla chiave di sottoscrizione nel campo area servizio riconoscimento vocale del componente LunarcomController nel pannello di controllo. Ad esempio, per l'area Stati Uniti occidentali digitare "westus".

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. Nella gerarchia espandere l'oggetto Lunarcom_Base facendo clic sulla freccia a sinistra. Eseguire quindi la stessa operazione per il relativo oggetto figlio, ovvero "terminale", come illustrato nell'immagine seguente.

20. Quando è selezionata l'opzione Lunarcom_Base, fare clic e trascinare il testo Lunarcom dalla gerarchia allo slot di testo di output nel componente LunarcomController nel pannello Inspector, come illustrato nell'immagine seguente.

21. Eseguire la stessa operazione con l'oggetto terminale nello slot del terminale e l'oggetto della luce di connessione allo slot del controller della luce di connessione.

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Fare clic sulla freccia accanto alla sezione dei pulsanti Lunarcom dello script LunarcomController nel pannello Inspector e modificare le dimensioni in 3. Premere INVIO o return. In questo modo vengono visualizzati tre nuovi campi elemento.

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Espandere i pulsanti Lunarcom facendo clic sulla freccia accanto alla gerarchia e usando lo stesso processo precedente, trascinare il MIC, il satellite e il GameObject Rocket rispettivamente sull'elemento 0, 1 e 2 riferimenti nel componente LunarcomController del Pannello di controllo.

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Selezionare l'oggetto Lunarcom_Base "nella gerarchia. Fare clic su Add Component nel pannello Inspector e cercare e selezionare Lunarcom Speech Recognizer. Ripetere gli stessi passaggi per aggiungere Lunarcom Wake Word Recognizer.

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. Nello slot della parola di riattivazione, digitare attiva terminale. Nello slot di Word ignorare, digitare ignora terminale.

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Compilare l'applicazione nel dispositivo

1. Aprire di nuovo la finestra impostazioni di compilazione passando a file > impostazioni di compilazione.

    ![images/mrlearning-Speech-CH1-2-Step1](images/mrlearning-speach-ch1-2-step1.jpg)

2. Assicurati che la scena che vuoi provare sia nell'elenco "Scenes in Build" (Scene nella compilazione) facendo clic sul pulsante "Add Open Scenes" (Aggiungi scene aperte).

3. Premere il pulsante Impostazioni lettore e passare a impostazioni di pubblicazione. In funzionalità abilitare: Internet, server client Internet, server client di rete privata, microfono e percezione spaziale.

4. Nelle stesse impostazioni del lettore passare a XR Settings e selezionare la realtà virtuale supportata su ON.

5. Scegli il pulsante Build (Compila) per avviare il processo di compilazione.

    ![mrlearning-Speech-CH1-2-passaggio 5](images/mrlearning-speach-ch1-2-step5.jpg)

6. Crea una nuova cartella per l'applicazione e assegna un nome alla cartella creata. Nell'immagine seguente è stata creata una cartella con il nome "App" per contenere l'applicazione. Fai clic su "Select Folder" (Seleziona cartella) per iniziare la compilazione nella cartella appena creata. Al termine della compilazione, puoi chiudere la finestra "Build Settings" (Impostazioni di compilazione) in Unity.

    ![mrlearning-Speech-CH1-2-passaggio 6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >se la compilazione ha esito negativo, prova a ripeterla o a riavviare Unity e a ripetere la compilazione. Se viene visualizzato un errore simile a "errore: CS0246 = Impossibile trovare il tipo o il nome dello spazio dei nomi" XX "(manca una direttiva using o un riferimento a un assembly?)", potrebbe essere necessario installare [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) .

7. Al termine della compilazione, apri la nuova cartella creata che contiene i file dell'applicazione appena compilata. Fare doppio clic sul file di soluzione ". sln" per aprire il file della soluzione in Visual Studio.

    >[!NOTE]
    >assicurati di aprire la cartella appena creata (ad esempio la cartella "App", se hai seguito le convenzioni di denominazione dei passaggi precedenti) perché un file con estensione sln denominato in modo analogo sarà presente al di fuori di tale cartella e non devi confonderlo con il file con estensione sln all'interno della cartella di compilazione. 

    ![mrlearning-Speech-CH1-2-STEP7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >se Visual Studio richiede di installare nuovi componenti, dedica qualche minuto per verificare che tutti i componenti prerequisiti siano installati come specificato nella pagina ["Installare gli strumenti"](install-the-tools.md)

8. Collega HoloLens 2 al PC con il cavo USB. Anche se le istruzioni in questa lezione presuppongono che distribuirai un test con un dispositivo HoloLens 2, puoi anche scegliere di distribuire nell'[emulatore HoloLens 2](using-the-hololens-emulator.md) oppure di creare un [pacchetto dell'app per il trasferimento locale](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

9. Prima della compilazione, assicurati che il dispositivo sia in modalità sviluppatore. Se questa è la prima volta che esegui la distribuzione nel dispositivo HoloLens 2, Visual Studio può richiedere di associare HoloLens 2 a un PIN. Segui [queste istruzioni](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) se devi abilitare la modalità sviluppatore o eseguire l'associazione con Visual Studio.

10. Configura Visual Studio per la compilazione nel dispositivo HoloLens 2 selezionando la configurazione "Release" e l'architettura "ARM".

    ![mrlearning-Speech-CH1-2-Step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. Il passaggio finale consiste nella compilazione nel dispositivo selezionando Debug>Avvia senza eseguire debug. Se selezioni "Avvia senza eseguire debug", l'applicazione viene avviata immediatamente nel dispositivo al termine della compilazione, ma senza che in Visual Studio vengano visualizzate le informazioni di debug. Questo significa anche che, mentre l'applicazione è in esecuzione sul dispositivo HoloLens 2, puoi disconnettere il cavo USB senza arrestare l'applicazione. Puoi anche selezionare Compila>Distribuisci soluzione per distribuire l'applicazione nel dispositivo senza che venga avviata automaticamente.

    ![mrlearning-Speech-CH1-2-STEP11. JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>Lezione completata

Il riconoscimento vocale è stato configurato nell'applicazione, con tecnologia Azure. Eseguire l'applicazione per verificare il corretto funzionamento di tutte le funzioni e funzionalità. Iniziare a indicare la parola di riattivazione digitata nel passaggio 22, attivare il terminale. Selezionare il pulsante del microfono per avviare il riconoscimento vocale. Inizia a pronunciare. Si noterà che le parole sono state trascritte nel terminale mentre si parla. Premere il pulsante microfono una seconda volta per arrestare il riconoscimento vocale. Per nascondere il terminale Lunarcom, è possibile ignorare il terminale. Nella lezione successiva verrà illustrato come passare in modo dinamico all'uso del riconoscimento vocale basato su dispositivo per le situazioni in cui l'SDK di sintesi vocale di Azure non è disponibile perché HoloLens 2 è offline.

[Esercitazione successiva: 2. aggiunta di una modalità offline per la traduzione vocale locale](mrlearning-speechSDK-ch2.md)
