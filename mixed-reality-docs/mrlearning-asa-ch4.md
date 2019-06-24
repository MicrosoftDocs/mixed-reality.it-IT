---
title: Modulo ASA Learning MR Azure ancoraggio spaziale su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326932"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="96cce-104">Photon (correggere me se si è errato)</span><span class="sxs-lookup"><span data-stu-id="96cce-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="96cce-105">In questa lezione,</span><span class="sxs-lookup"><span data-stu-id="96cce-105">In this lesson,</span></span> 

<span data-ttu-id="96cce-106">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="96cce-106">Objectives:</span></span>

* <span data-ttu-id="96cce-107">Informazioni su come _</span><span class="sxs-lookup"><span data-stu-id="96cce-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="96cce-108">Informazioni su come _</span><span class="sxs-lookup"><span data-stu-id="96cce-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="96cce-109">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="96cce-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="96cce-110">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="96cce-110">Setting Up Photon</span></span>

1. <span data-ttu-id="96cce-111">Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span><span class="sxs-lookup"><span data-stu-id="96cce-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="96cce-112">In questo modo sarà costituito l'immissione dei messaggio di posta elettronica e in uscita tramite alcuni passaggi di verifica.</span><span class="sxs-lookup"><span data-stu-id="96cce-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="96cce-114">Dopo che è stata effettuata l'iscrizione, fare clic su SDK.</span><span class="sxs-lookup"><span data-stu-id="96cce-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="96cce-115">Una volta in tale pagina, fare clic su "server" e assicurarsi che lo stato, "self-hosted."</span><span class="sxs-lookup"><span data-stu-id="96cce-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="96cce-116">Scorrere verso il basso e fare clic su "server", come illustrato nell'immagine secondo seguente.</span><span class="sxs-lookup"><span data-stu-id="96cce-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="96cce-119">In tal modo una casella di testo da visualizzare con etichette, "Leggi me."</span><span class="sxs-lookup"><span data-stu-id="96cce-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="96cce-120">Proseguo e leggerlo.</span><span class="sxs-lookup"><span data-stu-id="96cce-120">Go ahead and read it.</span></span> <span data-ttu-id="96cce-121">Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.</span><span class="sxs-lookup"><span data-stu-id="96cce-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="96cce-123">Fare doppio clic sulla cartella termine di download.</span><span class="sxs-lookup"><span data-stu-id="96cce-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="96cce-124">Una volta Esplora file viene aperto rivelando la cartella del SDK, copiare la cartella del SDK.</span><span class="sxs-lookup"><span data-stu-id="96cce-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="96cce-125">Il passaggio successivo, è possibile passare nell'unità c: windows e creare una nuova cartella denominata "server".</span><span class="sxs-lookup"><span data-stu-id="96cce-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="96cce-127">A questo punto aprire la cartella e incollare la cartella SDK copiato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="96cce-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="96cce-129">Una volta che viene completato, aprire la cartella SDK e passare a "Distribuisci", quindi "bin_Win64", quindi fare doppio clic su "controllo photon".</span><span class="sxs-lookup"><span data-stu-id="96cce-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="96cce-131">Nota: Se hai domande sull'indirizzo IP o eventuali altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti (come illustrato nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="96cce-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="96cce-133">Ora che il server è configurato e avviato, tornare al sito Web Photon e fare clic sull'icona del profilo (boxed nell'immagine seguente) e selezionare "applicazioni".</span><span class="sxs-lookup"><span data-stu-id="96cce-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="96cce-135">Creare un ID applicazione facendo clic sul pulsante "Crea una nuova app".</span><span class="sxs-lookup"><span data-stu-id="96cce-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="96cce-137">Selezionare "Photon RUN" nel menu a discesa in "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="96cce-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="96cce-138">Assegnargli un nome, (qualcosa che sarebbe ricordarsi).</span><span class="sxs-lookup"><span data-stu-id="96cce-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="96cce-139">In questo esempio è denominato "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="96cce-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="96cce-140">Al termine, fare clic su "Crea".</span><span class="sxs-lookup"><span data-stu-id="96cce-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="96cce-142">Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="96cce-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="96cce-143">Fare clic sull'ID dell'app e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="96cce-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="96cce-144">Incolla è in una posizione che facilmente accessibile.</span><span class="sxs-lookup"><span data-stu-id="96cce-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="96cce-146">Creare un nuovo progetto unity.</span><span class="sxs-lookup"><span data-stu-id="96cce-146">Create a new unity project.</span></span> <span data-ttu-id="96cce-147">Aprire l'Hub di Unity e fare clic su "nuovo".</span><span class="sxs-lookup"><span data-stu-id="96cce-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="96cce-148">Denominarla "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="96cce-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="96cce-149">Quindi fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="96cce-149">Then click create.</span></span> 

   > <span data-ttu-id="96cce-150">Nota: L'operazione può richiedere fino a 2 minuti per caricare, in base alla velocità del computer.</span><span class="sxs-lookup"><span data-stu-id="96cce-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="96cce-152">Nota: selezionare una posizione in cui salvare il progetto nel computer modificando l'opzione "location".</span><span class="sxs-lookup"><span data-stu-id="96cce-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="96cce-153">Salvarlo in una posizione si terrà conto e accedere in modo semplice.</span><span class="sxs-lookup"><span data-stu-id="96cce-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="96cce-154">Una volta che il progetto viene caricato, fare clic su "asset store".</span><span class="sxs-lookup"><span data-stu-id="96cce-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="96cce-155">Quindi, nella casella di ricerca illustrata nell'immagine seguente, digitare "Stato" e selezionare l'asset "Photon 2 in poi gratuito".</span><span class="sxs-lookup"><span data-stu-id="96cce-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="96cce-157">Scaricare e importare.</span><span class="sxs-lookup"><span data-stu-id="96cce-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="96cce-159">**Impostazione del progetto Unity**</span><span class="sxs-lookup"><span data-stu-id="96cce-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="96cce-160">scaricare un nuovo asset necessari per configurare Photon in Unity facendo [qui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="96cce-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="96cce-161">In Unity, fare clic sul menu di risorse e selezionare "Importa gli asset", quindi fare clic su "risorse personalizzate".</span><span class="sxs-lookup"><span data-stu-id="96cce-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="96cce-163">Selezionare il pacchetto Unity che appena scaricato dal collegamento specificato nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="96cce-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="96cce-164">Una volta che viene visualizzato il pulsante di importazione in Unity, selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96cce-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="96cce-166">Nota: ovunque è stato scaricato il pacchetto sarà dove le trovi.</span><span class="sxs-lookup"><span data-stu-id="96cce-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="96cce-167">L'immagine precedente non indicano dove si troveranno il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="96cce-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="96cce-168">Creare una nuova scena (può essere effettuata utilizzando controllo / comando + N o facendo clic su "file" e selezionare "nuova scena.").</span><span class="sxs-lookup"><span data-stu-id="96cce-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="96cce-169">Salvare la scena come "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="96cce-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="96cce-170">Nota: è possibile che venga visualizzato un messaggio popup che ha un aspetto simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="96cce-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="96cce-171">Per ora, semplicemente fare clic su "no".</span><span class="sxs-lookup"><span data-stu-id="96cce-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="96cce-173">In fare clic su "Toolkit di realtà mista" su "Aggiungi alla scena e configurare".</span><span class="sxs-lookup"><span data-stu-id="96cce-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="96cce-175">Una volta completata, un nuovo file di configurazione apparirà, offrendo la possibilità di personalizzare il profilo.</span><span class="sxs-lookup"><span data-stu-id="96cce-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="96cce-176">Fare clic su "copia e personalizzare".</span><span class="sxs-lookup"><span data-stu-id="96cce-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="96cce-178">Scorrere verso il basso e deselezionare l'opzione "Abilita sistema di diagnostica".</span><span class="sxs-lookup"><span data-stu-id="96cce-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="96cce-179">Ciò renderà più facile configurare questo progetto.</span><span class="sxs-lookup"><span data-stu-id="96cce-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="96cce-181">Aprire le impostazioni di compilazione (controllo + MAIUSC + B).</span><span class="sxs-lookup"><span data-stu-id="96cce-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="96cce-182">Si noti che il programma è attualmente impostato con la piattaforma "PC, Mac e Linux in modo autonomo".</span><span class="sxs-lookup"><span data-stu-id="96cce-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="96cce-183">Per questo progetto, impostare la piattaforma sia "universal windows platform."</span><span class="sxs-lookup"><span data-stu-id="96cce-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="96cce-184">Selezionarlo e fare clic su "switch piattaforma".</span><span class="sxs-lookup"><span data-stu-id="96cce-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="96cce-186">Al termine, fare clic sulla casella con la dicitura "aggiungere scene Apri".</span><span class="sxs-lookup"><span data-stu-id="96cce-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="96cce-187">A questo punto passare al pannello di controllo e verificare che la casella di controllo a destra di "realtà virtuale supportati" (come illustrato nell'immagine seguente) è selezionata.</span><span class="sxs-lookup"><span data-stu-id="96cce-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="96cce-189">Nota: Assicurarsi anche che la casella di controllo accanto a "scene/HLSharedProjectMain" sia selezionata anche.</span><span class="sxs-lookup"><span data-stu-id="96cce-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="96cce-190">In "impostazioni di pubblicazione" nel Pannello di controllo scorrere fino alla "funzionalità" e verificare che siano contrassegnate solo le caselle di controllo seguenti:</span><span class="sxs-lookup"><span data-stu-id="96cce-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="96cce-191">client Internet</span><span class="sxs-lookup"><span data-stu-id="96cce-191">internet client</span></span>
- <span data-ttu-id="96cce-192">server client Internet</span><span class="sxs-lookup"><span data-stu-id="96cce-192">internet client server</span></span>
- <span data-ttu-id="96cce-193">server dei client di rete privata</span><span class="sxs-lookup"><span data-stu-id="96cce-193">private network client server</span></span>
- <span data-ttu-id="96cce-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="96cce-194">camera/webcam</span></span>
- <span data-ttu-id="96cce-195">Microfono</span><span class="sxs-lookup"><span data-stu-id="96cce-195">microphone</span></span>

21. <span data-ttu-id="96cce-196">Come passaggio 12, il passaggio successivo, è possibile importare un altro pacchetto personalizzato denominato "Della lezione 2", che può essere scaricato da [qui]. [lesson2.unitypackage inserire qui il collegamento] Importare tale pacchetto.</span><span class="sxs-lookup"><span data-stu-id="96cce-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="96cce-198">A questo punto, nel Pannello di progetto, passare alla cartella "prefabs", poiché in passaggi successivi è necessario implementare alcuni prefabs nella scena.</span><span class="sxs-lookup"><span data-stu-id="96cce-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="96cce-199">Nella cartella "prefabs", fare clic e trascinare il prefab, "DebugWindow" nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="96cce-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="96cce-200">Al termine, salvare il progetto (fare clic su file, quindi di salvare o CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="96cce-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="96cce-202">Nota: È possibile notare un messaggio popup visualizzato fare clic su di prefab, in cui viene richiesto su Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="96cce-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="96cce-203">Perché saranno necessarie, fare clic su "Importa TMP Essentials".</span><span class="sxs-lookup"><span data-stu-id="96cce-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="96cce-205">**Ci si connette più utenti**</span><span class="sxs-lookup"><span data-stu-id="96cce-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="96cce-206">Come passaggio 22, nella cartella "prefabs" nel Pannello di progetto, il passaggio successivo è per trascinare e rilasciare il prefab "NetworkLobby" in per la gerarchia.</span><span class="sxs-lookup"><span data-stu-id="96cce-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="96cce-208">Quando si apre il prefab padre, "NetworkLobby", verrà visualizzato un prefab, elemento figlio "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="96cce-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="96cce-209">Con essa selezionate, passare al pannello di controllo e fare clic su "Aggiungi componente".</span><span class="sxs-lookup"><span data-stu-id="96cce-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="96cce-210">Cercare "PhotonView" e aggiungere il componente.</span><span class="sxs-lookup"><span data-stu-id="96cce-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="96cce-212">Creare un nuovo oggetto gioco vuoto nella gerarchia di (a destra fare clic nella gerarchia e selezionare "vuota").</span><span class="sxs-lookup"><span data-stu-id="96cce-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="96cce-213">Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, "PhotonUser."</span><span class="sxs-lookup"><span data-stu-id="96cce-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="96cce-215">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="96cce-215">Congratulations</span></span>



