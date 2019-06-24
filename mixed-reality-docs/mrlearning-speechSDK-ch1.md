# <a name="speech-sdk-learning-module"></a>Modulo di apprendimento di Speech SDK

In questa esercitazione si creerà un'applicazione di realtà mista che esamina l'uso di Azure Cognitive Services Speech SDK con 2 HoloLens. Al termine di questa serie di esercitazioni, è possibile usare il microfono del dispositivo per trascrivere riconoscimento vocale in tempo reale, tradurre i comandi vocali in altre lingue e sfruttare funzionalità intento del SDK Speech per comprendere i comandi vocali tramite intelligenza artificiale.

Obiettivi:

- Descrive come integrare Azure Speech SDK in un'applicazione 2 HoloLens
- Informazioni su come usare i comandi vocali
- Informazioni su come usare le funzionalità di riconoscimento vocale

## <a name="instructions"></a>Istruzioni

### <a name="getting-started"></a>Attività iniziali

1. Avviare Unity e creare un nuovo progetto. Immettere il nome del progetto "Speech SDK Learning modulo". Scegliere un percorso per la posizione in cui salvare il progetto. Quindi fare clic su "Crea progetto".

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> Nota: Assicurarsi che il modello sia impostato su "3D", come illustrato nell'immagine precedente.

2. Scaricare il [Toolkit di realtà mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity creare un pacchetto e salvarlo in una cartella nel PC. Importare il pacchetto nel progetto Unity. Per istruzioni dettagliate su come eseguire questa operazione, vedi [lezione di modulo di base 1](mrlearning-base-ch1.md). 

3. Scaricare e importare di Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) per il pacchetto di asset di Unity. Importare il pacchetto di Speech SDK facendo clic su "risorse", selezionare "Importa pacchetto", quindi selezionando "pacchetto personalizzato". Trovare il pacchetto di Speech SDK scaricato in precedenza e aprirlo per iniziare il processo di importazione. 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. Nella finestra popup successiva, fare clic su "Importa" per avviare l'importazione del pacchetto Speech SDK. Verificare che tutti gli elementi vengono controllati, come illustrato nell'immagine seguente.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. Scaricare il [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) pacchetto di asset. Il pacchetto di asset Lunarcom è una raccolta di risorse e gli script sviluppati per questa serie lezione per dimostrare un uso pratico di Speech SDK di Azure. Si tratta di un terminale di comandi vocali che verrà infine interagiscono con l'esperienza di assembly lunare modulo sviluppata nel [esercitazione di modulo di Base.](mrlearning-base-ch6.md)
6. Importare il pacchetto di asset Lunarcom nel progetto Unity, seguendo una procedura simile che è stata eseguita per importare i Toolkit di realtà mista e Speech SDK.
7. Configurare il Toolkit di realtà mista (MRTK). A tale scopo, fare clic sul pannello "Toolkit di realtà mista" nella parte superiore della finestra di e quindi selezionare "Aggiungi alla scena e configura".

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. Scena avrà alcuni nuovi elementi in essa dal MRTK. Salva scena con un nome diverso, fare clic su "file", quindi "Salva con nome" e denominare la scena "SpeechScene". 

   > Nota: Se si preme il pulsante play nella scena, dopo aver aggiunto il MRTK al progetto, e non viene attivata la modalità "play", si potrebbe essere necessario riavviare Unity. 

9. Con l'oggetto "MixedRealityToolkit" selezionato nella gerarchia, fare clic su "copia e personalizzare" nel Pannello di controllo.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. Anche nel Pannello di controllo (con l'oggetto "MixedRealityToolkit" selezionato nella gerarchia), disabilitare il sistema di diagnostica deselezionando la casella a destra di "Attiva diagnostica System".

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. Nel Pannello di progetto, espandere la cartella "Lunarcom" e trascinare il prefab "Lunarcom_Base" nella gerarchia.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. Selezionare l'oggetto "Lunarcom_Base" nella gerarchia e verificare che la posizione è impostata su x = 0, y = 0 e z = 0, nonché la rotazione impostata su x = 0, y = 0 e z = 0. Impostare la scalabilità necessaria per leggere x = 0,008, y = 0,008 e z = 0,01.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. Fare clic su "Aggiungi componente" e cercare e selezionare "LunarcomController." Questo script è incluso nel pack Lunarcom asset a cui è stato importato nel passaggio 6.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. Per connettere l'App nell'app per servizi cognitivi di Azure, è necessario immettere una chiave di sottoscrizione"" noto anche come "Chiave API" per il servizio riconoscimento vocale. Seguire le istruzioni in [questo collegamento](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) per ottenere una chiave di sottoscrizione gratuita. Dopo avere ottenuto la chiave di sottoscrizione, immetterlo nel campo "Chiave API del servizio riconoscimento vocale" del componente "LunarcomController" nel Pannello di controllo, come illustrato nell'immagine seguente.

15. Immettere l'area in cui si è scelto quando è effettuata l'iscrizione per la chiave di sottoscrizione nel campo "Area di servizio riconoscimento vocale" del componente "LunarcomController" nel Pannello di controllo.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. Nella gerarchia, espandere l'oggetto "Lunarcom_Base" facendo clic sulla freccia a sinistra di essa, quindi eseguire la stessa operazione per l'oggetto figlio, "Terminal", come illustrato nell'immagine seguente.

17. Mentre "Lunarcom_Base" è selezionato, fare clic e trascinare "Lunarcom Text" dalla gerarchia di allo slot di "Testo di Output" nel componente "LunarcomController" nel Pannello di controllo, come illustrato nell'immagine seguente.
18. Eseguire ora la stessa operazione con l'oggetto "Terminal" slot di "terminal" e l'oggetto "Connessione leggero" allo slot di "Connessione Light Controller".

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. Fare clic sulla freccia accanto alla sezione "Lunarcom pulsanti" dello script "LunarcomController" nel Pannello di controllo e modificare le dimensioni a 3 e premere il tasto INVIO sulla tastiera. Questa operazione comporta tre nuovi campi "Elemento" venga visualizzato.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. Espandere i pulsanti"Lunarcom" facendo clic sulla freccia accanto a esso nella gerarchia e, usando lo stesso processo come sopra, trascinare il Mic, Satellite e Rocket gameobject ai riferimenti rispettivamente nel componente "LunarcomController" elemento 0, 1 e 2 di Pannello di controllo. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. Selezionare l'oggetto "Lunarcom_Base" nella gerarchia. Fare clic su "Add Component" nel Pannello di controllo e cercare e selezionare "LunarcomWakeWordRecognizer."

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. Nello slot di "Word riattivazione", digitare "Activate Terminal". Inoltre, nello slot di "Chiudere Word", digitare "Dismiss Terminal".

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>Lezione completata

Aver configurato il riconoscimento vocale nell'applicazione, con tecnologia Azure! Eseguire l'applicazione per assicurarsi che tutte le funzioni sono funzioni correttamente. Iniziare con indicante che la parola di riattivazione digitato nel passaggio 22, "Activate Terminal". Selezionare quindi il pulsante del microfono per avviare il riconoscimento vocale e iniziare a parlare. Si noterà che le parole trascritte nel terminale, mentre si parla. Premere il pulsante del microfono una seconda volta per arrestare il riconoscimento vocale. Ad esempio "Ignora Terminal" per nascondere il terminale Lunarcom. Nella lezione successiva si apprenderà come passare in modo dinamico all'utilizzo di riconoscimento vocale basati sul dispositivo, per le situazioni in cui la vocale di Azure SDK non è disponibile a causa di 2 HoloLens in modalità offline.

[Lezione successiva: Speech SDK lezione 2](mrlearning-speechSDK-ch2.md)

