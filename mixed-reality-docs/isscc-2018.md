---
title: White paper fotocamera profondità - ISSCC 2018
description: White paper tecnico che illustrano la fotocamera profondità utilizzabili nel progetto Kinect per Azure e la prossima versione di HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: evento, iscc, visione artificiale, ricerca, kinect, hololens, profondità, indice delle figure
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601083"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="1e458-104">White paper fotocamera profondità - ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="1e458-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="1e458-105">**titolo:** Indice delle figure sensore con 3.5μm di demodulato 1Mpixel 65 nm BSI MHz 320 pixel ridimensionamento globale e la creazione di contenitori analogico</span><span class="sxs-lookup"><span data-stu-id="1e458-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="1e458-106">**Collaboratori:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Elkhatib Tamer, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Snow Dane, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, sillaba Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="1e458-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="1e458-107">**Presentato alla ISSCC 2018 e pubblicati in ISSCC Deg. Tech. Paper, febbraio 2018.**</span><span class="sxs-lookup"><span data-stu-id="1e458-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="1e458-108">C.</span><span class="sxs-lookup"><span data-stu-id="1e458-108">C.</span></span> <span data-ttu-id="1e458-109">Bamji e così via, "1Mpixel 65 nm BSI MHz 320 demodulato sensore indice delle figure con 3.5μm ridimensionamento globale pixel e analogico Binning," ISSCC gradi.</span><span class="sxs-lookup"><span data-stu-id="1e458-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="1e458-110">Tech.</span><span class="sxs-lookup"><span data-stu-id="1e458-110">Tech.</span></span> <span data-ttu-id="1e458-111">Paper, pagg. 94-95, febbraio 2018.</span><span class="sxs-lookup"><span data-stu-id="1e458-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="1e458-112">IEEE Esplora collegamento: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="1e458-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="1e458-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="1e458-113">© 2018 IEEE.</span></span> <span data-ttu-id="1e458-114">Utilizzo personale di questo materiale è consentito.</span><span class="sxs-lookup"><span data-stu-id="1e458-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="1e458-115">Autorizzazione da IEEE deve essere ottenuto per tutti gli altri usi, in qualsiasi contenuto multimediale corrente o futuro, tra cui ristampa/la ripubblicazione di questo materiale per scopi pubblicitari o promozionali, la creazione di nuovi works collettivo, per la rivendita o ridistribuzione agli elenchi, o i server o riutilizzo di qualsiasi componente protetto da copyright di questo miglioramento in altro funziona.</span><span class="sxs-lookup"><span data-stu-id="1e458-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="1e458-116">**Whitepaper:**</span><span class="sxs-lookup"><span data-stu-id="1e458-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="1e458-117">![Anteprima di white paper](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="1e458-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="1e458-118">Scarica il white paper di profondità della fotocamera</span><span class="sxs-lookup"><span data-stu-id="1e458-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
