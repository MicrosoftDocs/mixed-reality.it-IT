## <a name="lesson-2"></a>Lezione 2

Nella lezione 2, si aggiungerà una modalità non in linea che ci consentirà di eseguire la traduzione vocale-locale quando non è possibile connettersi al servizio di Azure e ne verrà *simulare* uno stato disconnesso.

1. Selezionare l'oggetto "Lunarcom_Base" nella gerarchia e fare clic su "Add Component" nel Pannello di controllo. Cercare e selezionare "Lunarcom Offline riconoscimento."

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. Fare clic sulla freccia in "LunarcomOfflineRecognizer" e selezionare "Abilitato". Questo sarà il progetto di agire come utente non dispone di connessione del programma. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. A questo punto, premere riprodurre sull'Editor di Unity ed eseguirne il test. Premere il microfono nell'angolo in basso a sinistra nella scena e iniziare a parlare. 

> Nota: poiché si passa alla modalità offline, la funzionalità di riattivazione Word è stata disabilitata. Pertanto, si dovrà fisicamente fare clic sul microfono ogni volta che si vuole che il riconoscimento vocale riconosciuto mentre offline. 

Di seguito è riportato un esempio di ciò che potrebbe essere scena simile:

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Lezione completata

È stata abilitata la modalità offline. A questo punto quando si è lontano da alcun mezzo di internet, è possibile comunque lavorare al progetto con Speech SDK! 

[Lezione successiva: SpeechSDK lezione 3](link placeholder)

