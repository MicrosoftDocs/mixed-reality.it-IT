## <a name="lesson-2"></a><span data-ttu-id="4e967-101">Lezione 2</span><span class="sxs-lookup"><span data-stu-id="4e967-101">Lesson 2</span></span>

<span data-ttu-id="4e967-102">Nella lezione 2, si aggiungerà una modalità non in linea che ci consentirà di eseguire la traduzione vocale-locale quando non è possibile connettersi al servizio di Azure e ne verrà *simulare* uno stato disconnesso.</span><span class="sxs-lookup"><span data-stu-id="4e967-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="4e967-103">Selezionare l'oggetto "Lunarcom_Base" nella gerarchia e fare clic su "Add Component" nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="4e967-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="4e967-104">Cercare e selezionare "Lunarcom Offline riconoscimento."</span><span class="sxs-lookup"><span data-stu-id="4e967-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="4e967-106">Fare clic sulla freccia in "LunarcomOfflineRecognizer" e selezionare "Abilitato".</span><span class="sxs-lookup"><span data-stu-id="4e967-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="4e967-107">Questo sarà il progetto di agire come utente non dispone di connessione del programma.</span><span class="sxs-lookup"><span data-stu-id="4e967-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="4e967-109">A questo punto, premere riprodurre sull'Editor di Unity ed eseguirne il test.</span><span class="sxs-lookup"><span data-stu-id="4e967-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="4e967-110">Premere il microfono nell'angolo in basso a sinistra nella scena e iniziare a parlare.</span><span class="sxs-lookup"><span data-stu-id="4e967-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="4e967-111">Nota: poiché si passa alla modalità offline, la funzionalità di riattivazione Word è stata disabilitata.</span><span class="sxs-lookup"><span data-stu-id="4e967-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="4e967-112">Pertanto, si dovrà fisicamente fare clic sul microfono ogni volta che si vuole che il riconoscimento vocale riconosciuto mentre offline.</span><span class="sxs-lookup"><span data-stu-id="4e967-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="4e967-113">Di seguito è riportato un esempio di ciò che potrebbe essere scena simile:</span><span class="sxs-lookup"><span data-stu-id="4e967-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="4e967-115">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="4e967-115">Congratulations</span></span>

<span data-ttu-id="4e967-116">È stata abilitata la modalità offline.</span><span class="sxs-lookup"><span data-stu-id="4e967-116">The offline mode has been enabled!</span></span> <span data-ttu-id="4e967-117">A questo punto quando si è lontano da alcun mezzo di internet, è possibile comunque lavorare al progetto con Speech SDK!</span><span class="sxs-lookup"><span data-stu-id="4e967-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="4e967-118">Lezione successiva: SpeechSDK lezione 3</span><span class="sxs-lookup"><span data-stu-id="4e967-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

