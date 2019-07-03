# <a name="getting-unity-ready-for-development"></a>Operazioni preliminari per lo sviluppo di Unity 

In questa esercitazione, è informazioni su come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui l'importazione del Toolkit di realtà mista, configurare le impostazioni di compilazione e preparazione la scena.

Obiettivi:

- Configurare Unity per lo sviluppo di applicazioni

- Importare Mixed Reality Toolkit

- Preparare la scena di progetto

### <a name="instructions"></a>Istruzioni

1. Scaricare e salvare il pacchetto unity Toolkit di realtà mista facendo [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. In Unity, fare clic sul menu di risorse e selezionare Import Package, quindi fare clic sul pacchetto personalizzato.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selezionare il pacchetto Unity che appena scaricato dal collegamento specificato nel passaggio 1. Una volta che viene visualizzata la finestra popup di importazione in Unity, fare clic sul pulsante Importa per avviare l'importazione. L'importazione di MRTK potrebbe richiedere alcuni minuti.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: Il pacchetto scaricato si trova nella cartella locale in cui il file è stato salvato. L'immagine precedente non indicano dove si troveranno il pacchetto.

4. Creare una nuova scena. TIl può essere eseguita facendo clic sul File e selezionando una nuova scena"). Salvare la scena come HLSharedProjectMain.

> Nota: è possibile che venga visualizzato un messaggio popup che ha un aspetto simile all'immagine seguente. Per il momento, fare clic su No.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Nel Toolkit di realtà mista, fare clic su Aggiungi alla scena e Configure.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una volta completata, un nuovo file di configurazione viene visualizzata, offrendo la possibilità di personalizzare il profilo. Fare clic su copia e personalizzare.

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Scorrere verso il basso e deselezionare Abilita Siagnostics sistema se si desidera nascondere la finestra di diagnostica. È consigliabile mantenere la finestra di diagnostica abilitati durante lo sviluppo di applicazioni per monitorare le prestazioni e la sua disabilitazione durante le dimostrazioni di produzione o di applicazione. 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare al File -> Build Settings. Si noti che il programma è attualmente impostato con la piattaforma autonomo PC, Mac e Linux. Per lo sviluppo di HoloLens 2, impostare la piattaforma sia (Universal Windows Platform). Selezionarlo e fare clic sulla piattaforma del commutatore.![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Al termine, fare clic sulla casella di testo aggiungere scene Open. Ora passare al pannello di controllo e assicurarsi che sia selezionata la casella di controllo a destra del virtuale realtà supportati (come illustrato nell'immagine seguente). Assicurarsi anche che la casella di controllo accanto a scene/HLSharedProjectMain viene selezionata anche come illustrato nell'immagine seguente.![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Nella sezione Impostazioni di pubblicazione nel Pannello di controllo, scorrere fino alla capacità e verificare che le caselle di controllo seguenti siano contrassegnate:![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importare il pacchetto personalizzato chiamato SharingAssetCollection che può essere scaricato [qui.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Nel Pannello di progetto, passare alla cartella Prefabs. In passaggi successivi si implementa alcuni prefabs nella scena. Nella cartella Prefabs, fare clic e trascinare il prefab, DebugWindow nella gerarchia. Al termine, salvare il progetto da clckin File, quindi salvare o premere CTRL + + S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Nota: È possibile notare un messaggio popup visualizzato fare clic su di prefab, in cui viene richiesto su Essentials TMP. Fare clic su Importa TMP Essentials, se necessario. Se viene visualizzato questo popup, si potrebbe essere necessario eliminare il prefab dalla gerarchia e trascinare nuovamente all'interno della gerarchia per evitare potenziali errori correlati al testo.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Lezione completata

Il progetto Unity è ora pronto per Photon. Nelle esercitazioni prossime, verrà compilata su questa scena e il progetto Unity verso un'esperienza completa condiviso.

[Esercitazione successiva: Ci si connette più utenti](mrlearning-sharing(photon)-ch3.md)

