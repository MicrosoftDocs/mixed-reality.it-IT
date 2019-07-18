### <a name="getting-unity-ready-for-development"></a><span data-ttu-id="292b2-101">Preparazione di Unity per lo sviluppo</span><span class="sxs-lookup"><span data-stu-id="292b2-101">Getting Unity ready for development</span></span> 


<span data-ttu-id="292b2-102">Questa esercitazione illustra come preparare e configurare Unity per lo sviluppo di applicazioni, tra cui l'importazione del Toolkit di realtà mista, la configurazione delle impostazioni di compilazione e la preparazione della scena.</span><span class="sxs-lookup"><span data-stu-id="292b2-102">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="292b2-103">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="292b2-103">Objectives:</span></span>

- <span data-ttu-id="292b2-104">Configurare Unity per lo sviluppo di applicazioni</span><span class="sxs-lookup"><span data-stu-id="292b2-104">Configure Unity for application development</span></span>

- <span data-ttu-id="292b2-105">Importare Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="292b2-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="292b2-106">Preparare la scena del progetto</span><span class="sxs-lookup"><span data-stu-id="292b2-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="292b2-107">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="292b2-107">Instructions</span></span>

1. <span data-ttu-id="292b2-108">Scaricare e salvare il pacchetto di Unity del Toolkit di realtà misto facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="292b2-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="292b2-109">In Unity fare clic sul menu assets e selezionare Import Package, quindi fare clic su Custom Package.</span><span class="sxs-lookup"><span data-stu-id="292b2-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="292b2-111">Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="292b2-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="292b2-112">Una volta visualizzata la finestra popup importa in Unity, fare clic sul pulsante Import (importa) per avviare l'importazione.</span><span class="sxs-lookup"><span data-stu-id="292b2-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="292b2-113">L'importazione del MRTK può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="292b2-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="292b2-115">Nota: Il pacchetto scaricato si trova nella cartella locale in cui è stato salvato il file.</span><span class="sxs-lookup"><span data-stu-id="292b2-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="292b2-116">L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="292b2-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="292b2-117">Creare una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="292b2-117">Create a new scene.</span></span> <span data-ttu-id="292b2-118">A tale scopo, fare clic su file e selezionare nuova scena.</span><span class="sxs-lookup"><span data-stu-id="292b2-118">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="292b2-119">Salvare la scena come HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="292b2-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="292b2-120">Nota: è possibile che venga visualizzato un popup simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="292b2-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="292b2-121">Per il momento, fare clic su No.</span><span class="sxs-lookup"><span data-stu-id="292b2-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="292b2-123">In Mixed Reality Toolkit fare clic su Aggiungi a scena e configurare.</span><span class="sxs-lookup"><span data-stu-id="292b2-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="292b2-125">Una volta completato, viene visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo.</span><span class="sxs-lookup"><span data-stu-id="292b2-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="292b2-126">Fare clic su copia e Personalizza.</span><span class="sxs-lookup"><span data-stu-id="292b2-126">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="292b2-130">Scorrere verso il basso e deselezionare Abilita sistema di diagnostica se si desidera nascondere la finestra di diagnostica.</span><span class="sxs-lookup"><span data-stu-id="292b2-130">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="292b2-131">È consigliabile mantenere la finestra di diagnostica abilitata durante lo sviluppo di applicazioni per monitorare le prestazioni e disabilitarla durante le dimostrazioni di produzione o di applicazioni.</span><span class="sxs-lookup"><span data-stu-id="292b2-131">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="292b2-133">Per aprire le impostazioni di compilazione, premere CTRL + MAIUSC + B o passare a file-> impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="292b2-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="292b2-134">Si noti che il programma è attualmente impostato nel computer, Mac e piattaforma autonoma Linux.</span><span class="sxs-lookup"><span data-stu-id="292b2-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="292b2-135">Per lo sviluppo HoloLens 2, impostare la piattaforma da piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="292b2-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="292b2-136">Selezionarlo e fare clic su switch Platform.</span><span class="sxs-lookup"><span data-stu-id="292b2-136">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="292b2-138">Al termine, fare clic sulla casella di testo Aggiungi scene aperte.</span><span class="sxs-lookup"><span data-stu-id="292b2-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="292b2-139">Passare ora al pannello Inspector e verificare che la casella di controllo a destra della realtà virtuale supportata (come illustrato nell'immagine seguente) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="292b2-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="292b2-140">Assicurarsi inoltre che anche la casella di controllo accanto a Scenes/HLSharedProjectMain sia selezionata, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="292b2-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="292b2-142">Nella sezione impostazioni di pubblicazione del pannello Inspector scorrere fino a funzionalità e verificare che le caselle di controllo seguenti siano contrassegnate:</span><span class="sxs-lookup"><span data-stu-id="292b2-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="292b2-144">Importare il pacchetto personalizzato denominato SharingAssetCollection che può essere scaricato [qui.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="292b2-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="292b2-146">Nel pannello progetto passare alla cartella prefabbricates.</span><span class="sxs-lookup"><span data-stu-id="292b2-146">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="292b2-147">Nei passaggi successivi vengono implementati alcuni prefabbricati nella scena.</span><span class="sxs-lookup"><span data-stu-id="292b2-147">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="292b2-148">Nella cartella prefabbricati, fare clic e trascinare la finestra prefabbricata, debug nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="292b2-148">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="292b2-149">Al termine, salvare il progetto facendo clic su file, quindi su Salva o premere CTRL + S.</span><span class="sxs-lookup"><span data-stu-id="292b2-149">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="292b2-151">Nota: È possibile che venga visualizzato un messaggio popup quando si fa clic sul prefabbricato, che richiede informazioni su TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="292b2-151">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="292b2-152">Fare clic su Importa TMP Essentials in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="292b2-152">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="292b2-153">Se viene visualizzato questo popup, potrebbe essere necessario eliminare il prefabbricato dalla gerarchia e trascinarlo nella gerarchia per evitare potenziali errori correlati al testo.</span><span class="sxs-lookup"><span data-stu-id="292b2-153">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="292b2-155">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="292b2-155">Congratulations</span></span>

<span data-ttu-id="292b2-156">Il progetto Unity è ora pronto per Photon.</span><span class="sxs-lookup"><span data-stu-id="292b2-156">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="292b2-157">Nelle esercitazioni riportate di seguito verrà creata questa scena e il progetto Unity per un'esperienza condivisa completa.</span><span class="sxs-lookup"><span data-stu-id="292b2-157">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="292b2-158">[Esercitazione successiva: Connessione di più utenti](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="292b2-158">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

