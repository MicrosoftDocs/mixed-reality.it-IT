---
title: OpenXR
description: Provare l'API OpenXR 0,90 provvisorio con l'anteprima per sviluppatori di OpenXR realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realtà mista OpenXR Developer Preview
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603660"
---
# <a name="openxr"></a>OpenXR

OpenXR è uno standard e gratuita aperto da [Khronos](https://www.khronos.org/) che fornisce l'accesso nativo a un'ampia gamma di dispositivi da molti fornitori che si estendono sulle [spettro di realtà mista](mixed-reality.md).

Con OpenXR, è possibile compilare applicazioni destinate sia holographic dispositivi (ad esempio 2 di HoloLens) che consentono di posizionare contenuto digitale nel mondo reale, come se fosse non sono disponibili, nonché dispositivi immersivi (ad esempio le cuffie realtà mista di Windows per PC desktop) che nascondono la mondo fisico e sostituirla con un'esperienza digitale.  OpenXR consente di scrivere codice una volta che viene quindi portabile in un'ampia gamma di piattaforme hardware.

Lo standard OpenXR è attualmente in una fase provvisoria, con una specifica OpenXR 0,90 inizio rilasciata per commenti e suggerimenti.  Per altre informazioni su OpenXR, incluso l'accesso al [provisional spec 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) e [intestazioni](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), vedere il [pagina Khronos OpenXR](https://www.khronos.org/openxr/).

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Impostare l'anteprima per sviluppatori di OpenXR realtà mista

È possibile provare l'API OpenXR 0,90 provisional oggi stesso con l'anteprima per sviluppatori di OpenXR realtà mista.  Questo runtime di anteprima consente alle applicazioni destinate a API di OpenXR 0,90 per le cuffie immersive destinazione realtà mista di Windows sul desktop.  Se non si ha accesso per le cuffie, è possibile usare invece il simulatore di realtà mista di Windows.

Per iniziare a usare l'anteprima per sviluppatori di OpenXR realtà mista:

1. Verificare che Windows è in esecuzione almeno il 10 ottobre 2018 Update.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento di ottobre 2018 Update usando le [Assistente aggiornamento di Windows 10](https://www.microsoft.com/en-us/software-download/windows10).  Se lo si avventuroso, è possibile installare una [compilazione di Windows 10 Insider Preview](https://insider.windows.com).
1. Consente di impostare un visore VR realtà mista di Windows o per seguire le istruzioni [Abilita il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md).
1. Installare il [realtà mista OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Questa app ti permette di configurare con l'anteprima OpenXR runtime per Windows 10 ottobre 2018 Update o versione successiva.  Dopo aver installato l'app, il Windows Store consente di mantenere il runtime aggiornato.
1. Eseguire l'app mista realtà OpenXR Developer Preview dal menu Start e seguire le istruzioni per rendere il runtime attivo.  A breve, questa app sarà possibile esplorare anche altre informazioni di debug OpenXR.

![Realtà mista OpenXR Developer Preview app](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Supporto per Windows 10 ottobre 2018 Update

Per procedere con l'anteprima per sviluppatori di OpenXR realtà mista di Windows 10 ottobre 2018 Update (versione corrente di Windows), è necessario seguire alcuni passaggi aggiuntivi:

1. Seguire i passaggi precedenti per installare l'anteprima per sviluppatori di OpenXR realtà mista.
1. Per impostare l'anteprima per sviluppatori di OpenXR realtà mista come runtime OpenXR attivo del sistema, installare il [mista realtà OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-test-openxr-app"></a>Creazione di un test di app OpenXR

Il [hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR testare l'app viene illustrato l'utilizzo di varie parti dell'API.  È possibile seguire queste [istruzioni di creazione](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), che creerà l'app di test e le intestazioni OpenXR autonomamente.

## <a name="feedback"></a>Feedback

Per fornire il feedback il [specification OpenXR provvisorie 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visitare il [Khronos OpenXR forum](https://community.khronos.org/c/openxr), [canale Slack #openxr](https://khr.io/slack) e il [spec tracker problema](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Risoluzione dei problemi

Di seguito sono riportati alcuni suggerimenti sulla risoluzione dei problemi per l'anteprima per sviluppatori di OpenXR realtà mista.  Se si riscontrano altri problemi, visitare il [Khronos OpenXR forum](https://community.khronos.org/c/openxr) oppure [canale Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR non avvii per realtà mista di Windows

Se l'app OpenXR non si avvii la realtà mista di Windows durante l'esecuzione, l'anteprima per sviluppatori di OpenXR realtà mista non può essere impostato come il runtime attivo.  Assicurarsi di eseguire l'app mista realtà OpenXR Developer Preview e seguire le istruzioni per rendere il runtime attivo.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Non è possibile installare app OpenXR Developer Preview di realtà mista 

Verificare che Windows è in esecuzione almeno il 10 ottobre 2018 Update.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento di ottobre 2018 Update usando le [Assistente aggiornamento di Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Se l'installazione pulsante nell'app mista realtà OpenXR Developer Preview non esegue alcuna operazione in Windows 10 ottobre 2018 Aggiorna, il sistema potrebbe viene memorizzato nella cache i requisiti di sistema non aggiornato per l'app.  È possibile eseguire il comando `wsreset.exe` da un prompt dei comandi per cancellare la cache.

## <a name="see-also"></a>Vedere anche

* [Altre informazioni su OpenXR](https://www.khronos.org/openxr/)
* [Specifica di OpenXR provvisorie 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Riferimento all'API OpenXR provvisorie 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Intestazioni OpenXR provvisorie 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
