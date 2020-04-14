---
title: 'Case Study: lezioni dalla cucina di Lowe'
description: Il team di HoloLens desidera condividere alcune delle procedure consigliate derivate dal progetto HoloLens di Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Lowe, HoloLens, kitchen, case study
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278129"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Case Study: lezioni dalla cucina di Lowe

Il team di HoloLens desidera condividere alcune delle procedure consigliate derivate dal progetto HoloLens di Lowe. Di seguito è riportato un video della HoloLens di Lowe proiettato in occasione di 2016 Ignite.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Procedure consigliate per HoloLens di Lowe

I due video riguardano le procedure consigliate derivate dal progetto pilota HoloLens di Lowe che è stato in due negozi di Lowe a partire dal 2016 aprile. Gli argomenti principali sono:
* Ottimizzare le prestazioni per un dispositivo mobile
* Creare metodi UX con un frame olografico completo (seconda conversazione)
* Allineamento di precisione (secondo colloquio)
* Esperienze olografiche condivise (seconda conversazione)
* Interazione con i clienti (seconda conversazione)

## <a name="video-1"></a>Video 1

**Ottimizzare le prestazioni per un dispositivo mobile** HoloLens è un dispositivo senza tethering con tutte le operazioni di elaborazione eseguite nel dispositivo. Questa operazione richiede una piattaforma mobile e richiede un approccio simile alla creazione di applicazioni per dispositivi mobili. Microsoft consiglia di mantenere 60FPS per offrire agli utenti un'esperienza deliziosa per l'applicazione HoloLens. La presenza di FPS bassi può produrre ologrammi instabili.

Alcuni degli aspetti più importanti da considerare durante lo sviluppo in HoloLens sono l'ottimizzazione e la decimazione degli asset, usando shader personalizzati (disponibili gratuitamente in [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)). Un altro aspetto importante da considerare è misurare la frequenza dei fotogrammi dall'inizio del progetto. A seconda del progetto, l'ordine di visualizzazione degli asset può anche essere un grande collaboratore
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Video 2

**Creare metodi UX con un frame olografico completo** È importante comprendere la posizione degli ologrammi in un ambiente fisico. Con Lowe parliamo dei diversi metodi di UX che consentono agli utenti di osservare gli ologrammi in chiusura, pur continuando a osservare l'ambiente più ampio degli ologrammi.

**Allineamento di precisione** Per lo scenario di Lowe, era fondamentale per l'esperienza avere un allineamento di precisione degli ologrammi alla cucina fisica. Le tecniche consentono di garantire un'esperienza che consenta agli utenti di modificare l'ambiente fisico.

**Esperienze olografiche condivise** Le coppie rappresentano il modo principale in cui l'esperienza Lowe viene utilizzata. Una persona può modificare il contropiano e l'altra persona vedrà le modifiche. Abbiamo chiamato "esperienze condivise".

**Interazione con i clienti** I progettisti di Lowe non usano un HoloLens, ma devono vedere cosa vedono i clienti. Viene illustrato come acquisire le informazioni visualizzate dal cliente in un'applicazione UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
