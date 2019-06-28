<span data-ttu-id="2c579-101">**Operazioni preliminari per lo sviluppo di Unity**</span><span class="sxs-lookup"><span data-stu-id="2c579-101">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="2c579-102">In questa lezione si apprenderà come preparare e configurare Unity per lo sviluppo di app, inclusi l'importazione del Toolkit di realtà mista, configurare le impostazioni di compilazione e preparazione la scena.</span><span class="sxs-lookup"><span data-stu-id="2c579-102">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="2c579-103">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="2c579-103">Objectives:</span></span>

- <span data-ttu-id="2c579-104">Configurare Unity per lo sviluppo di app</span><span class="sxs-lookup"><span data-stu-id="2c579-104">Configure Unity for app development</span></span>

- <span data-ttu-id="2c579-105">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="2c579-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="2c579-106">Preparare la scena di progetto</span><span class="sxs-lookup"><span data-stu-id="2c579-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="2c579-107">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="2c579-107">Instructions</span></span>

1. <span data-ttu-id="2c579-108">Scaricare e salvare il pacchetto unity Toolkit di realtà mista facendo [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="2c579-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="2c579-109">In Unity, fare clic sul menu di risorse e selezionare "Importa pacchetto", quindi fare clic su "Custom Package".</span><span class="sxs-lookup"><span data-stu-id="2c579-109">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="2c579-111">Selezionare il pacchetto Unity che appena scaricato dal collegamento specificato nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="2c579-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="2c579-112">Una volta che viene visualizzata la finestra popup di importazione in Unity, fare clic sul pulsante Importa per avviare l'importazione.</span><span class="sxs-lookup"><span data-stu-id="2c579-112">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="2c579-113">L'importazione di MRTK potrebbe richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="2c579-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="2c579-115">Nota: Il pacchetto scaricato sarà nella cartella locale in cui il file è stato salvato.</span><span class="sxs-lookup"><span data-stu-id="2c579-115">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="2c579-116">L'immagine precedente non indicano dove si troveranno il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="2c579-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="2c579-117">Creare una nuova scena (questa operazione può essere eseguita facendo clic su "file" e selezionare "nuova scena").</span><span class="sxs-lookup"><span data-stu-id="2c579-117">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="2c579-118">Salvare la scena come "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="2c579-118">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="2c579-119">Nota: è possibile che venga visualizzato un messaggio popup che ha un aspetto simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="2c579-119">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="2c579-120">Per il momento, fare clic su "No".</span><span class="sxs-lookup"><span data-stu-id="2c579-120">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="2c579-122">In fare clic su "Toolkit di realtà mista" su "Aggiungi alla scena e configurare".</span><span class="sxs-lookup"><span data-stu-id="2c579-122">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="2c579-124">Una volta completata, un nuovo file di configurazione apparirà, offrendo la possibilità di personalizzare il profilo.</span><span class="sxs-lookup"><span data-stu-id="2c579-124">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="2c579-125">Fare clic su "copia e personalizzare".</span><span class="sxs-lookup"><span data-stu-id="2c579-125">Click "copy and customize."</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="2c579-129">Scorrere verso il basso e deselezionare l'opzione "Abilita sistema di diagnostica", se si vuole nascondere la finestra di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="2c579-129">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="2c579-130">È consigliabile mantenere la finestra di diagnostica abilitati durante lo sviluppo di app per monitorare le prestazioni e la sua disabilitazione durante le dimostrazioni di produzione o di applicazione.</span><span class="sxs-lookup"><span data-stu-id="2c579-130">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="2c579-132">Aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare al File > Build Settings.</span><span class="sxs-lookup"><span data-stu-id="2c579-132">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="2c579-133">Si noti che il programma è attualmente impostato con la piattaforma "PC, Mac e Linux in modo autonomo".</span><span class="sxs-lookup"><span data-stu-id="2c579-133">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="2c579-134">Per lo sviluppo di HoloLens 2, impostare la piattaforma sia "Universal Windows Platform."</span><span class="sxs-lookup"><span data-stu-id="2c579-134">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="2c579-135">Selezionarlo e fare clic su "switch piattaforma".</span><span class="sxs-lookup"><span data-stu-id="2c579-135">Select it and click "switch platform."</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="2c579-137">Al termine, fare clic sulla casella con la dicitura "aggiungere scene Apri".</span><span class="sxs-lookup"><span data-stu-id="2c579-137">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="2c579-138">A questo punto passare al pannello di controllo e verificare che la casella di controllo a destra di "realtà virtuale supportati" (come illustrato nell'immagine seguente) è selezionata.</span><span class="sxs-lookup"><span data-stu-id="2c579-138">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="2c579-139">Inoltre assicurarsi che sia selezionata anche la casella di controllo accanto a "scene/HLSharedProjectMain", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="2c579-139">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="2c579-141">Nella sezione "Impostazioni di pubblicazione" sezione lo scorrimento del Pannello di controllo fino alla "Funzionalità" e verificare che le caselle di controllo seguenti siano contrassegnate:</span><span class="sxs-lookup"><span data-stu-id="2c579-141">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="2c579-143">Importare il pacchetto personalizzato denominato "SharingAssetCollection", che può essere scaricato [qui.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="2c579-143">Import the custom package called "SharingAssetCollection" which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="2c579-144">A questo punto, nel Pannello di progetto, passare alla cartella "prefabs", poiché in passaggi successivi è necessario implementare alcuni prefabs nella scena.</span><span class="sxs-lookup"><span data-stu-id="2c579-144">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="2c579-145">Nella cartella "prefabs", fare clic e trascinare il prefab, "DebugWindow" nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="2c579-145">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="2c579-146">Al termine, salvare il progetto (fare clic sul file, quindi salvare, o premere CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="2c579-146">Once finished, save the project (click file, then save, or press control+S)</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="2c579-148">Nota: È possibile notare un messaggio popup visualizzato fare clic su di prefab, in cui viene richiesto su Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="2c579-148">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="2c579-149">Perché saranno necessarie, fare clic su "Importa TMP Essentials".</span><span class="sxs-lookup"><span data-stu-id="2c579-149">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="2c579-150">Se viene visualizzato questo popup, si potrebbe essere necessario eliminare il prefab dalla gerarchia e trascinare nuovamente all'interno della gerarchia per evitare potenziali errori correlati al testo.</span><span class="sxs-lookup"><span data-stu-id="2c579-150">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="2c579-152">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="2c579-152">Congratulations</span></span>

<span data-ttu-id="2c579-153">Il progetto Unity è ora pronto per Photon.</span><span class="sxs-lookup"><span data-stu-id="2c579-153">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="2c579-154">Nelle prossime lezioni, viene creata al momento questa scena e il progetto Unity verso un'esperienza completa condiviso.</span><span class="sxs-lookup"><span data-stu-id="2c579-154">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="2c579-155">[Lezione successiva: Sharing(photon) lezione 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="2c579-155">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

