---
title: .NET Remoting holographic Player
description: Il lettore di .NET Remoting Holographic è un'app complementare che si connette a PC App e giochi che supportano la comunicazione remota Holographic. .NET Remoting holographic streaming holographic contenuto da un PC per i Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, servizi remoti .NET Remoting Holographic
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605000"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="58140-105">.NET Remoting holographic Player</span><span class="sxs-lookup"><span data-stu-id="58140-105">Holographic Remoting Player</span></span>

<span data-ttu-id="58140-106">Il lettore di .NET Remoting Holographic è un'app complementare che si connette a PC App e giochi che supportano la comunicazione remota Holographic.</span><span class="sxs-lookup"><span data-stu-id="58140-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="58140-107">.NET Remoting holographic streaming holographic contenuto da un PC per i Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="58140-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="58140-108">Il giocatore remoto Holographic utilizzabile solo con le app a PC che sono progettate specificamente per supportare la comunicazione remota Holographic.</span><span class="sxs-lookup"><span data-stu-id="58140-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="58140-109">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="58140-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="58140-110">La connessione al lettore Holographic .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="58140-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="58140-111">Seguire le istruzioni dell'app per la connessione al lettore di .NET Remoting Holographic.</span><span class="sxs-lookup"><span data-stu-id="58140-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="58140-112">È necessario immettere l'indirizzo IP del dispositivo HoloLens, che è possibile visualizzare nella schermata principale del giocatore remoto come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="58140-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![.NET Remoting holographic Player](images/holographicremotingplayer.png)

<span data-ttu-id="58140-114">Ogni volta che viene visualizzata la schermata principale, si saprà che non è un'app connessa.</span><span class="sxs-lookup"><span data-stu-id="58140-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="58140-115">Si noti che la connessione di .NET remoting holographic **non crittografato**.</span><span class="sxs-lookup"><span data-stu-id="58140-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="58140-116">È necessario utilizzare sempre Holographic servizi remoti tramite una connessione Wi-Fi sicura attendibili.</span><span class="sxs-lookup"><span data-stu-id="58140-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="58140-117">Qualità e prestazioni</span><span class="sxs-lookup"><span data-stu-id="58140-117">Quality and Performance</span></span>

<span data-ttu-id="58140-118">Qualità e prestazioni della tua esperienza possono variare in base tre fattori:</span><span class="sxs-lookup"><span data-stu-id="58140-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="58140-119">**Esperienza olografica stai lavorando** -App che eseguono il rendering di contenuto ad alta risoluzione o estremamente dettagliata può essere necessario un computer più veloce o più veloce connessione wireless.</span><span class="sxs-lookup"><span data-stu-id="58140-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="58140-120">**Hardware del PC** -il PC deve essere in grado di eseguire e codificare l'esperienza olografica a 60 fotogrammi al secondo.</span><span class="sxs-lookup"><span data-stu-id="58140-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="58140-121">Per una scheda grafica, è consigliabile in genere un GeForce GTX 970 o AMD Radeon R9 290 o migliore.</span><span class="sxs-lookup"><span data-stu-id="58140-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="58140-122">Anche in questo caso, l'esperienza di particolare può richiedere una carta di fascia bassa o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="58140-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="58140-123">**La connessione Wi-Fi** -l'esperienza olografica viene trasmesso tramite Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="58140-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="58140-124">Usare una rete veloce di congestione bassa per ottimizzare la qualità.</span><span class="sxs-lookup"><span data-stu-id="58140-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="58140-125">Usa un PC che è connesso tramite un cavo Ethernet, anziché Wi-Fi, può anche migliorare la qualità.</span><span class="sxs-lookup"><span data-stu-id="58140-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="58140-126">Diagnostica</span><span class="sxs-lookup"><span data-stu-id="58140-126">Diagnostics</span></span>

<span data-ttu-id="58140-127">Per misurare la qualità della connessione, ad esempio **"abilitare la diagnostica"** mentre nella schermata principale del lettore Remoting Holographic.</span><span class="sxs-lookup"><span data-stu-id="58140-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="58140-128">Quando è abilitata la diagnostica, l'app verrà illustrato:</span><span class="sxs-lookup"><span data-stu-id="58140-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="58140-129">**FPS** : il numero medio di fotogrammi sottoposti a rendering il giocatore di .NET remoting è la ricezione e il rendering al secondo.</span><span class="sxs-lookup"><span data-stu-id="58140-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="58140-130">La soluzione ideale è 60 FPS.</span><span class="sxs-lookup"><span data-stu-id="58140-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="58140-131">**Latenza** -la quantità media di tempo necessario per un frame passare da PC a di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="58140-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="58140-132">Minore è la migliore.</span><span class="sxs-lookup"><span data-stu-id="58140-132">The lower the better.</span></span> <span data-ttu-id="58140-133">Ciò dipende in gran parte della rete Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="58140-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="58140-134">Quando è attiva la schermata principale, è possibile dire **"disabilitare la diagnostica"** per disattivare la diagnostica.</span><span class="sxs-lookup"><span data-stu-id="58140-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="58140-135">Requisiti di sistema:</span><span class="sxs-lookup"><span data-stu-id="58140-135">PC System Requirements</span></span>
* <span data-ttu-id="58140-136">I PC **necessario** essere in esecuzione Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="58140-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="58140-137">È consigliabile un GeForce GTX 970 o AMD Radeon R9 290 o una scheda grafica migliorata.</span><span class="sxs-lookup"><span data-stu-id="58140-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="58140-138">È consigliabile che Connetti il tuo PC alla rete tramite ethernet per ridurre il numero di hop Wireless.</span><span class="sxs-lookup"><span data-stu-id="58140-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="58140-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="58140-139">See Also</span></span>
* [<span data-ttu-id="58140-140">Condizioni di licenza software di .NET remoting holographic</span><span class="sxs-lookup"><span data-stu-id="58140-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="58140-141">Informativa sulla Privacy di Microsoft</span><span class="sxs-lookup"><span data-stu-id="58140-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
