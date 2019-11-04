---
title: Modulo MR Learning ASA-Azure Spatial Anchor su HoloLens 2
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437797"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="f662e-104">Photon (Correggi se sbaglio)</span><span class="sxs-lookup"><span data-stu-id="f662e-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="f662e-105">In questa lezione,</span><span class="sxs-lookup"><span data-stu-id="f662e-105">In this lesson,</span></span> 

<span data-ttu-id="f662e-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f662e-106">Objectives:</span></span>

* <span data-ttu-id="f662e-107">Scopri come _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="f662e-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="f662e-108">Scopri come _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="f662e-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="f662e-109">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f662e-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="f662e-110">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="f662e-110">Setting Up Photon</span></span>

1. <span data-ttu-id="f662e-111">Configurare un account [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="f662e-111">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="f662e-112">Questa operazione consiste nell'imputare il messaggio di posta elettronica e nell'eseguire alcuni passaggi di verifica.</span><span class="sxs-lookup"><span data-stu-id="f662e-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="f662e-114">Dopo aver effettuato l'iscrizione, fare clic su SDK.</span><span class="sxs-lookup"><span data-stu-id="f662e-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="f662e-115">Una volta visualizzata la pagina, fare clic su "Server" e assicurarsi che "self hosted".</span><span class="sxs-lookup"><span data-stu-id="f662e-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="f662e-116">Scorrere quindi verso il basso e fare clic su "Server", come illustrato nella seconda immagine riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="f662e-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="f662e-119">Verrà visualizzata una casella di testo con etichetta "Read me".</span><span class="sxs-lookup"><span data-stu-id="f662e-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="f662e-120">Procediamo con la lettura.</span><span class="sxs-lookup"><span data-stu-id="f662e-120">Go ahead and read it.</span></span> <span data-ttu-id="f662e-121">Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.</span><span class="sxs-lookup"><span data-stu-id="f662e-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="f662e-123">Al termine del download, fare doppio clic sulla cartella.</span><span class="sxs-lookup"><span data-stu-id="f662e-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="f662e-124">Una volta visualizzata la cartella SDK, in Esplora file copiare la cartella SDK.</span><span class="sxs-lookup"><span data-stu-id="f662e-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="f662e-125">Il passaggio successivo consiste nell'accedere all'unità C: di Windows e creare una nuova cartella denominata "Server".</span><span class="sxs-lookup"><span data-stu-id="f662e-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="f662e-127">Aprire quindi la cartella e incollare la cartella SDK copiata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f662e-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="f662e-129">Al termine, aprire la cartella SDK e passare a "deploy" (Distribuisci), quindi a "bin_Win64", quindi fare doppio clic su "PHOTON Control".</span><span class="sxs-lookup"><span data-stu-id="f662e-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="f662e-131">Nota: in caso di domande relative all'indirizzo IP o ad altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="f662e-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="f662e-133">Ora che il server è stato configurato e avviato, tornare al sito Web di Photon e fare clic sull'icona del profilo (boxed nell'immagine seguente) e selezionare "applicazioni".</span><span class="sxs-lookup"><span data-stu-id="f662e-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="f662e-135">Per creare un ID applicazione, fare clic sul pulsante "crea una nuova app".</span><span class="sxs-lookup"><span data-stu-id="f662e-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="f662e-137">Selezionare "Photon RUN" dal menu a discesa in "Photon Type".</span><span class="sxs-lookup"><span data-stu-id="f662e-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="f662e-138">Assegnare quindi un nome (un elemento da ricordare).</span><span class="sxs-lookup"><span data-stu-id="f662e-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="f662e-139">In questo esempio è stato denominato "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="f662e-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="f662e-140">Al termine, fare clic su "Crea".</span><span class="sxs-lookup"><span data-stu-id="f662e-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="f662e-142">Al termine, tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="f662e-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="f662e-143">Fare clic sull'ID app e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="f662e-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="f662e-144">Incollare è possibile accedere facilmente a.</span><span class="sxs-lookup"><span data-stu-id="f662e-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="f662e-146">Creare un nuovo progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f662e-146">Create a new unity project.</span></span> <span data-ttu-id="f662e-147">Aprire Hub Unity e fare clic su "nuovo".</span><span class="sxs-lookup"><span data-stu-id="f662e-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="f662e-148">Denominarlo "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="f662e-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="f662e-149">Quindi fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="f662e-149">Then click create.</span></span> 

   > <span data-ttu-id="f662e-150">Nota: il caricamento può richiedere fino a 2 minuti, in base alla velocità del computer.</span><span class="sxs-lookup"><span data-stu-id="f662e-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="f662e-152">Nota: selezionare una posizione in cui salvare il progetto nel computer modificando l'opzione "percorso".</span><span class="sxs-lookup"><span data-stu-id="f662e-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="f662e-153">Salvarlo in una posizione che si ricorda e avere accesso facile a.</span><span class="sxs-lookup"><span data-stu-id="f662e-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="f662e-154">Una volta caricato il progetto, fare clic su "assets Store".</span><span class="sxs-lookup"><span data-stu-id="f662e-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="f662e-155">Quindi, nella casella di ricerca mostrata nell'immagine seguente digitare "PUN" e selezionare l'asset "Photon PUN-2 FREE".</span><span class="sxs-lookup"><span data-stu-id="f662e-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="f662e-157">Scaricare e importare</span><span class="sxs-lookup"><span data-stu-id="f662e-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="f662e-159">**Configurazione del progetto Unity**</span><span class="sxs-lookup"><span data-stu-id="f662e-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="f662e-160">scaricare un nuovo asset necessario per configurare Photon in Unity facendo clic [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f662e-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="f662e-161">In Unity fare clic sul menu assets e selezionare "Import assets", quindi fare clic su "asset personalizzati".</span><span class="sxs-lookup"><span data-stu-id="f662e-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="f662e-163">Selezionare il pacchetto Unity appena scaricato dal collegamento fornito nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="f662e-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f662e-164">Quando il pulsante Importa viene visualizzato in Unity, fare clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="f662e-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="f662e-166">Nota: ogni volta che il pacchetto è stato scaricato in, sarà possibile trovarlo.</span><span class="sxs-lookup"><span data-stu-id="f662e-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="f662e-167">L'immagine precedente non rappresenta la posizione in cui si troverà il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="f662e-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="f662e-168">Creare una nuova scena. questa operazione può essere eseguita usando Ctrl/Comando + N oppure facendo clic su "file" e selezionando "nuova scena".</span><span class="sxs-lookup"><span data-stu-id="f662e-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="f662e-169">Salvare la scena come "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="f662e-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="f662e-170">Nota: è possibile che venga visualizzato un popup simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="f662e-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="f662e-171">Per il momento, è sufficiente fare clic su "No".</span><span class="sxs-lookup"><span data-stu-id="f662e-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="f662e-173">In "Mixed Reality Toolkit" fare clic su "Aggiungi a scena e configura".</span><span class="sxs-lookup"><span data-stu-id="f662e-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="f662e-175">Al termine, verrà visualizzato un nuovo file di configurazione che consente di scegliere di personalizzare il profilo.</span><span class="sxs-lookup"><span data-stu-id="f662e-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="f662e-176">Fare clic su "copia e Personalizza".</span><span class="sxs-lookup"><span data-stu-id="f662e-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="f662e-178">Scorrere verso il basso e deselezionare "Abilita sistema di diagnostica".</span><span class="sxs-lookup"><span data-stu-id="f662e-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="f662e-179">Questo renderà più semplice configurare questo progetto.</span><span class="sxs-lookup"><span data-stu-id="f662e-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="f662e-181">Aprire le impostazioni di compilazione (CTRL + MAIUSC + B).</span><span class="sxs-lookup"><span data-stu-id="f662e-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="f662e-182">Si noti che il programma è attualmente impostato nella piattaforma "PC, Mac e Linux standalone".</span><span class="sxs-lookup"><span data-stu-id="f662e-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="f662e-183">Per questo progetto, impostare la piattaforma su "Universal Windows Platform".</span><span class="sxs-lookup"><span data-stu-id="f662e-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="f662e-184">Selezionarlo e fare clic su "switch Platform".</span><span class="sxs-lookup"><span data-stu-id="f662e-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="f662e-186">Al termine, fare clic sulla casella "Aggiungi scene aperte".</span><span class="sxs-lookup"><span data-stu-id="f662e-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="f662e-187">Passare ora al pannello Inspector e verificare che la casella di controllo a destra di "Virtual Reality supported" (come illustrato nell'immagine seguente) sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="f662e-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="f662e-189">Nota: Assicurarsi inoltre che sia selezionata anche la casella di controllo accanto a "Scenes/HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="f662e-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="f662e-190">In "impostazioni di pubblicazione" nel pannello Inspector scorrere verso il basso fino a "funzionalità" e verificare che siano contrassegnate solo le caselle di controllo seguenti:</span><span class="sxs-lookup"><span data-stu-id="f662e-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="f662e-191">client Internet</span><span class="sxs-lookup"><span data-stu-id="f662e-191">internet client</span></span>
- <span data-ttu-id="f662e-192">Server client Internet</span><span class="sxs-lookup"><span data-stu-id="f662e-192">internet client server</span></span>
- <span data-ttu-id="f662e-193">Server client di rete privata</span><span class="sxs-lookup"><span data-stu-id="f662e-193">private network client server</span></span>
- <span data-ttu-id="f662e-194">fotocamera/webcam</span><span class="sxs-lookup"><span data-stu-id="f662e-194">camera/webcam</span></span>
- <span data-ttu-id="f662e-195">microfono</span><span class="sxs-lookup"><span data-stu-id="f662e-195">microphone</span></span>

21. <span data-ttu-id="f662e-196">Analogamente al passaggio 12, il passaggio successivo consiste nell'importare un altro pacchetto personalizzato denominato "della lezione 2" che è possibile scaricare [qui.] [collegamento della lezione 2. file unitypackage Tools Importare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="f662e-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="f662e-198">A questo punto, nel pannello progetto passare alla cartella "prefabbricates", poiché nei prossimi passaggi verranno implementate alcune prefabbricati nella scena.</span><span class="sxs-lookup"><span data-stu-id="f662e-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="f662e-199">Nella cartella "prefabbricates" fare clic e trascinare la prefabbricata "DebugWindow" nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f662e-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="f662e-200">Al termine, salvare il progetto (fare clic su file, quindi su Salva o CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="f662e-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="f662e-202">Nota: è possibile che venga visualizzato un popup quando si fa clic sulla prefabbricata, in cui viene chiesto di installare TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="f662e-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f662e-203">Fare clic su "Importa TMP Essentials" perché saranno necessari.</span><span class="sxs-lookup"><span data-stu-id="f662e-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="f662e-205">**Connessione di più utenti**</span><span class="sxs-lookup"><span data-stu-id="f662e-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="f662e-206">Come il passaggio 22, nella cartella "prefabbricates" del pannello del progetto, il passaggio successivo consiste nel trascinare e rilasciare il prefabbricato "NetworkLobby" nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f662e-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="f662e-208">Quando si apre la prefabbricata padre, "NetworkLobby", dovrebbe essere visualizzata una prefabbricata figlio, "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="f662e-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="f662e-209">Selezionando questa opzione, passare al pannello di controllo e fare clic su "Aggiungi componente".</span><span class="sxs-lookup"><span data-stu-id="f662e-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="f662e-210">Cercare "PhotonView" e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="f662e-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="f662e-212">Creare un nuovo oggetto gioco vuoto nella gerarchia di (fare clic con il pulsante destro del mouse nella gerarchia e selezionare "Empty").</span><span class="sxs-lookup"><span data-stu-id="f662e-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="f662e-213">Verificare che il posizionamento sia impostato su x = 0, y = 0, z = 0 e denominare l'oggetto "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="f662e-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="f662e-215">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f662e-215">Congratulations</span></span>



