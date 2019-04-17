---
title: Modalità di gioco Unity
description: Usa la modalità Play nell'editor di Unity per visualizzare in anteprima le modifiche in un dispositivo senza distribuirvi un'app.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, .NET remoting, holographic .NET remoting, Windows Media player holographic .NET remoting
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597823"
---
# <a name="unity-play-mode"></a><span data-ttu-id="fd89b-104">Modalità di gioco Unity</span><span class="sxs-lookup"><span data-stu-id="fd89b-104">Unity Play Mode</span></span>

<span data-ttu-id="fd89b-105">Un modo rapido per lavorare al progetto di Unity è in modalità "riprodurre".</span><span class="sxs-lookup"><span data-stu-id="fd89b-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="fd89b-106">Esegue l'app in locale nell'editor di Unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="fd89b-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="fd89b-107">Unity Usa Holographic .NET Remoting per fornire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale.</span><span class="sxs-lookup"><span data-stu-id="fd89b-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="fd89b-108">Modalità di gioco Unity con .NET Remoting Holographic</span><span class="sxs-lookup"><span data-stu-id="fd89b-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="fd89b-109">Con .NET Remoting Holographic, si può provare l'app in HoloLens, mentre è in esecuzione nell'editor di Unity nel PC.</span><span class="sxs-lookup"><span data-stu-id="fd89b-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="fd89b-110">Sguardo, gesti, vocale e mapping spaziale di input viene inviato da di HoloLens al computer.</span><span class="sxs-lookup"><span data-stu-id="fd89b-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="fd89b-111">Fotogrammi sottoposti a rendering vengono quindi inviati nuovamente di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd89b-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="fd89b-112">Questo è un ottimo modo per rapidamente il debug dell'app senza compilazione e distribuzione di un progetto completo.</span><span class="sxs-lookup"><span data-stu-id="fd89b-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="fd89b-113">Nella finestra di HoloLens, andare al **Microsoft Store** e installare il **[Holographic Player .NET Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span><span class="sxs-lookup"><span data-stu-id="fd89b-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="fd89b-114">Nel HoloLens, avviare il **Holographic Remoting Player** app.</span><span class="sxs-lookup"><span data-stu-id="fd89b-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="fd89b-115">In Unity, passare al **finestra** dal menu **emulazione Holographic**.</span><span class="sxs-lookup"><span data-stu-id="fd89b-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="fd89b-116">Impostare **modalità di emulazione** al **remoto al dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="fd89b-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="fd89b-117">Per la **computer remoto**, immettere l'indirizzo IP di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd89b-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="fd89b-118">Fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="fd89b-118">Click **Connect**.</span></span> <span data-ttu-id="fd89b-119">Si noterà **lo stato della connessione** passare alla **connesso** e visualizzare la schermata, passare vuota nella finestra di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd89b-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="fd89b-120">Fare clic sui **riprodurre** pulsante per avviare la modalità di riproduzione e l'esperienza dell'app in di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd89b-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="fd89b-121">.NET Remoting holographic richiede una connessione veloce di PC e Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="fd89b-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="fd89b-122">Visualizzare [Player Remoting Holographic](holographic-remoting-player.md) per i dettagli completi.</span><span class="sxs-lookup"><span data-stu-id="fd89b-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="fd89b-123">Per ottenere risultati ottimali, verificare che l'app imposta correttamente i [concentrarsi punto](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="fd89b-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="fd89b-124">In questo modo Holographic .NET Remoting per adattarsi meglio scena alla latenza della connessione wireless.</span><span class="sxs-lookup"><span data-stu-id="fd89b-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd89b-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fd89b-125">See Also</span></span>
* [<span data-ttu-id="fd89b-126">.NET Remoting holographic Player</span><span class="sxs-lookup"><span data-stu-id="fd89b-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
