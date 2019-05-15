---
title: L'aggiornamento dell'applicazione SteamVR per realtà mista di Windows
description: Procedure consigliate per l'aggiornamento dell'applicazione SteamVR per ottimizzare la compatibilità con le cuffie realtà mista di Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilità
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597853"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="12596-104">L'aggiornamento dell'applicazione SteamVR per realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="12596-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="12596-105">E invita gli sviluppatori per testare e ottimizzare le proprie esperienze SteamVR per eseguire in auricolari realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="12596-106">Questa documentazione include miglioramenti comuni possono rendere gli sviluppatori per garantire che l'esperienza funziona correttamente sulle realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="12596-107">Istruzioni di installazione iniziali</span><span class="sxs-lookup"><span data-stu-id="12596-107">Initial setup instructions</span></span>

<span data-ttu-id="12596-108">Per avviare il test orizzontale gioco o nell'app su marca di realtà mista di Windows assicurarsi di seguire prima i [Guida introduttiva.](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="12596-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="12596-109">Modelli di controller</span><span class="sxs-lookup"><span data-stu-id="12596-109">Controller Models</span></span>
1. <span data-ttu-id="12596-110">Se l'app esegue il rendering dei modelli di controller:</span><span class="sxs-lookup"><span data-stu-id="12596-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="12596-111">Usare il [modelli controller movimento di realtà mista di Windows](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="12596-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="12596-112">Usare IVRRenderModel::GetComponentState ottenere locale Trasforma alle parti componente (ad es.</span><span class="sxs-lookup"><span data-stu-id="12596-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="12596-113">Puntatore posa)</span><span class="sxs-lookup"><span data-stu-id="12596-113">Pointer pose)</span></span>
2. <span data-ttu-id="12596-114">Esperienze che dispongono di una nozione di mano dovrebbe essere hint dell'input API per differenziare i controller [(ad esempio Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="12596-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="12596-115">Controlli</span><span class="sxs-lookup"><span data-stu-id="12596-115">Controls</span></span>

<span data-ttu-id="12596-116">Quando si progetta o modificando il layout del controllo tenere presente il seguente set di comandi riservati:</span><span class="sxs-lookup"><span data-stu-id="12596-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="12596-117">Facendo clic verso il basso il **thumbstick sinistro e destro analogico** è riservato per il **Dashboard Steam**.</span><span class="sxs-lookup"><span data-stu-id="12596-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="12596-118">Il **pulsante Windows** restituirà sempre agli utenti in Windows Mixed Reality home.</span><span class="sxs-lookup"><span data-stu-id="12596-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="12596-119">Se possibile, il valore predefinito per thumb stilizzata basa teletrasporto in modo che corrisponda il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teletrasporto comportamento</span><span class="sxs-lookup"><span data-stu-id="12596-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="12596-120">Le descrizioni comandi e l'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="12596-120">Tooltips and UI</span></span>

<span data-ttu-id="12596-121">Molti giochi di realtà virtuale sfruttano i vantaggi di descrizioni comandi di controller di animazione e sovrapposizioni di insegnare agli utenti i comandi più importanti per i propri giochi o app.</span><span class="sxs-lookup"><span data-stu-id="12596-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="12596-122">Durante l'ottimizzazione dell'applicazione per realtà mista di Windows si consiglia di esaminare questa parte della tua esperienza per assicurarsi che le descrizioni comandi eseguire il mapping per i modelli di controller di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="12596-123">Anche se sono presenti i punti durante l'utilizzo in cui si visualizzano le immagini dei controller di assicurarsi di fornire le immagini aggiornate con i controller di movimento di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="12596-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="12596-124">Haptics</span></span>

<span data-ttu-id="12596-125">Inizia con la [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics sono ora supportati per usufruire di SteamVR realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="12596-126">Se l'app SteamVR o il gioco include già il supporto per haptics, che dovrebbe funzionare (con alcuna attività aggiuntiva) con [controller di movimento di realtà mista di Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="12596-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="12596-127">I controller di movimento di realtà mista di Windows usano un motore haptics standard, a differenza di attuatori lineari trovato in alcuni altri SteamVR movimento controller, che può comportare un'esperienza utente leggermente diversa-rispetto al previsto.</span><span class="sxs-lookup"><span data-stu-id="12596-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="12596-128">È quindi consigliabile test e ottimizzazione della progettazione haptics con i controller del movimento di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="12596-129">Ad esempio, impulsi aptico talvolta brevi (da 5 a 10 ms) sono meno evidente nei controller di movimento di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="12596-130">Per produrre un impulso più evidente, provare a usare l'invio di un più lungo "fare clic su" (40 70ms) per concedere il motore più tempo per creare rapidamente prima indicato alla potenza nuovamente.</span><span class="sxs-lookup"><span data-stu-id="12596-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="12596-131">Avvio delle App SteamVR dal menu Start realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="12596-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="12596-132">Per esperienze di realtà virtuale distribuite tramite Steam, abbiamo [aggiornata la realtà mista di Windows per la versione SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) con la versione più recente [Windows Insider](https://insider.windows.com) RS5 voli in modo che i titoli SteamVR ora visualizzati di Dal menu Start realtà mista di Windows in "tutte le app" elenco automaticamente.</span><span class="sxs-lookup"><span data-stu-id="12596-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="12596-133">Con le versioni di software installate, i clienti possono ora avviare titoli SteamVR direttamente da all'interno di realtà mista di Windows home senza rimuovere le cuffie.</span><span class="sxs-lookup"><span data-stu-id="12596-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="12596-134">Logo di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="12596-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="12596-135">Per visualizzare il supporto di realtà mista di Windows per il titolo, passare al collegamento "Modifica pagina Store" nella pagina di destinazione dell'App, fare clic sulla scheda "Le informazioni di base" e scorrere verso il basso "Virtuale Reality".</span><span class="sxs-lookup"><span data-stu-id="12596-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="12596-136">Deselezionare l'opzione di "nascondere realtà mista di Windows" e quindi pubblicarla nello store.</span><span class="sxs-lookup"><span data-stu-id="12596-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="12596-137">Bug e feedback</span><span class="sxs-lookup"><span data-stu-id="12596-137">Bugs and feedback</span></span>

<span data-ttu-id="12596-138">Commenti e suggerimenti sono estremamente utile se si desidera migliorare l'esperienza SteamVR realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="12596-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="12596-139">Inviare tutti i commenti e suggerimenti e bug tramite la [Hub di Feedback Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span><span class="sxs-lookup"><span data-stu-id="12596-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="12596-140">Ecco alcune [suggerimenti su come rendere il tuo feedback SteamVR utile come possibili](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span><span class="sxs-lookup"><span data-stu-id="12596-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="12596-141">Se hai domande o commenti per condividere, è possibile anche contattare Microsoft sul nostro [forum di Steam](http://steamcommunity.com/app/719950/discussions/).</span><span class="sxs-lookup"><span data-stu-id="12596-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="12596-142">Domande frequenti e risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="12596-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="12596-143">Se si verificano problemi generali di configurazione o la tua esperienza di riproduzione [consultare i passaggi di risoluzione dei problemi più recenti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span><span class="sxs-lookup"><span data-stu-id="12596-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="12596-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12596-144">See also</span></span>
* [<span data-ttu-id="12596-145">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="12596-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="12596-146">Cronologia dei driver di controller visore VR e movimento</span><span class="sxs-lookup"><span data-stu-id="12596-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="12596-147">Realtà mista di Windows minimo PC compatibilità alle linee guida hardware</span><span class="sxs-lookup"><span data-stu-id="12596-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)