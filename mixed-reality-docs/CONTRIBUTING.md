---
title: Istruzioni per i contributi
description: Come contribuire alla documentazione della realtà mista di Windows.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516161"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Contributo alla documentazione per gli sviluppatori di Microsoft Mixed Reality

Il [repository pubblico per la documentazione per gli sviluppatori di Microsoft Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs) Eventuali articoli creati o modificati in questo repository **saranno visibili al pubblico.** 

I documenti di realtà mista di Windows sono ora disponibili nella piattaforma docs.microsoft.com, che usa Markdown di GitHub (con le funzionalità di Markdig). In pratica, il contenuto modificato in questo repository viene trasformato in pagine formattate e stilizzate visualizzate https://docs.microsoft.com/windows/mixed-reality in. 

In questa pagina vengono illustrati i passaggi e le linee guida di base per i contributi, oltre a collegamenti alle nozioni di base di Markdown. Grazie per il contributo.

## <a name="before-you-start"></a>Prima di iniziare

Se non si ha già un account, è necessario [creare un account github](https://github.com/join).

>[!NOTE]
>Se si è un dipendente Microsoft, collegare il proprio account GitHub al proprio alias Microsoft nel [portale Open source Microsoft](https://repos.opensource.microsoft.com/). Unisciti alle organizzazioni **"Microsoft"** e **"MicrosoftDocs"** .

Quando si configura l'account GitHub, si consigliano anche le precauzioni di sicurezza seguenti:
- Creare una [password complessa per l'account github](https://github.com/settings/admin).
- Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).
- Salvare i [codici di ripristino](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.
- Aggiornare le [impostazioni del profilo pubblico](https://github.com/settings/profile).
   - Impostare il nome e prendere in considerazione l'impostazione del *messaggio di posta elettronica pubblico* in modo che *non venga visualizzato l'indirizzo di posta elettronica*
   - Si consiglia di caricare un'immagine del profilo, in quanto verrà visualizzata un'anteprima nelle pagine di docs a cui si collabora.
- Se si prevede di usare un flusso di lavoro della riga di comando, è consigliabile impostare [git Credential Manager per Windows in](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) modo da non dover immettere la password ogni volta che si crea un contributo.

L'esecuzione di questi passaggi è importante, poiché il sistema di pubblicazione è associato a GitHub e verrà elencato come autore o collaboratore per ogni articolo usando l'alias GitHub.

## <a name="editing-an-existing-article"></a>Modifica di un articolo esistente

Usare il flusso di lavoro seguente per apportare aggiornamenti a *un articolo esistente* tramite GitHub in un Web browser:

1. Passare all'articolo che si vuole modificare nella cartella "Mixed-Reality-docs".
2. Selezionare il pulsante modifica (icona a matita) in alto a destra. Verrà automaticamente creato un ramo eliminabile dal ramo ' Master '.

   ![Modificare un articolo.](images/editpage.png)
3. Modificare il contenuto dell'articolo (vedere ["Nozioni di base di Markdown"](#markdown-basics) di seguito per informazioni aggiuntive).
4. Aggiornare i metadati come pertinente all'inizio di ogni articolo:
   * titolo Si tratta del titolo della pagina che viene visualizzato nella scheda del browser quando viene visualizzato l'articolo. Poiché questa operazione viene usata per l'indicizzazione e l'ottimizzazione, non è necessario modificare il titolo a meno che non sia necessario (sebbene questo sia meno critico prima che la documentazione diventi pubblica).
   * Descrizione Scrivere una breve descrizione del contenuto dell'articolo. Questa operazione favorisce la SEO e l'individuazione.
   * autore Se si è il proprietario principale della pagina, aggiungere qui l'alias GitHub.
   * ms. Author: Se si è il proprietario principale della pagina, aggiungere qui l'alias Microsoft (non è necessario @microsoft.com, solo l'alias).
   * ms. Data: Aggiornare la data se si aggiunge contenuto principale alla pagina, ma non per correzioni quali chiarimenti, formattazione, grammatica o ortografia.
   * Parole Parole chiave che facilitano il SEO (ottimizzazione del motore di ricerca). Aggiungere parole chiave, separate da una virgola e uno spazio, specifiche dell'articolo (ma senza punteggiatura dopo l'ultima parola chiave nell'elenco); non è necessario aggiungere parole chiave globali che si applicano a tutti gli articoli, perché sono gestite altrove. 
5. Una volta completate le modifiche apportate all'articolo, scorrere verso il basso e fare clic sul pulsante **Proponi modifica file** .
6. Nella pagina successiva fare clic su **Crea richiesta pull** per unire il ramo creato automaticamente in ' Master '.
7. Ripetere i passaggi precedenti per il prossimo articolo che si desidera modificare.

## <a name="creating-a-new-article"></a>Creazione di un nuovo articolo

Usare il flusso di lavoro seguente per *creare nuovi articoli* nel repository della documentazione tramite GitHub in un Web browser:

1. Creare un fork dal ramo ' Master ' di MicrosoftDocs/Mixed-Reality (usando il pulsante **fork** in alto a destra).

   ![Creare un fork del ramo master.](images/forkbranch.png)
2. Nella cartella "Mixed-Reality-docs" fare clic sul pulsante **Crea nuovo file** in alto a destra.
3. Creare un nome di pagina per l'articolo (usare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere ". MD"

   ![Assegnare un nome alla nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Assicurarsi di creare il nuovo articolo dall'interno della cartella "mixed-Real-docs". Per confermare questo problema, verificare la presenza di "/Mixed-Reality-docs/" nella nuova riga nome file.

4. Nella parte superiore della nuova pagina aggiungere il blocco di metadati seguente:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Compilare i campi dei metadati pertinenti in base alle istruzioni riportate nella [sezione precedente](#editing-an-existing-article).
6. Scrivere il contenuto dell'articolo usando le [nozioni fondamentali di Markdown](#markdown-basics)
7. Aggiungere una `## See also` sezione nella parte inferiore dell'articolo con i collegamenti ad altri articoli pertinenti.
8. Al termine, fare clic su Esegui **commit nuovo file**.
9. Fare clic su **nuova richiesta pull** e unire il ramo ' Master ' del fork in MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi la modalità corretta).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Nozioni fondamentali su Markdown

Le risorse seguenti consentiranno di apprendere come modificare la documentazione utilizzando il linguaggio markdown:

- [Nozioni fondamentali su Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Poster di riferimento Markdown-at-Glance](images/MarkdownPoster.pdf)
- [Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Aggiunta di tabelle

A causa del modo in cui le tabelle docs.microsoft.com stili, non avranno bordi o stili personalizzati, anche se si prova a usare CSS inline. Sembra funzionare per un breve periodo di tempo, ma alla fine la piattaforma eliminerà lo stile dalla tabella. Pianificare in anticipo e semplificare le tabelle. [Ecco un sito che semplifica la semplicità delle tabelle Markdown](http://www.tablesgenerator.com/markdown_tables).

L' [estensione docs Markdown per Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) rende inoltre semplice la generazione di tabelle se si usa [Visual Studio Code (vedere di seguito)](#using-visual-studio-code) per modificare la documentazione.

### <a name="adding-images"></a>Aggiunta di immagini

È necessario caricare le immagini nella cartella "mixed-Real-docs/images" del repository e quindi farvi riferimento in modo appropriato nell'articolo. Le immagini verranno automaticamente visualizzate a dimensione completa, il che significa che se l'immagine è di grandi dimensioni, riempirà tutta la larghezza dell'articolo. È quindi consigliabile pre-dimensionare le immagini prima di caricarle. La larghezza consigliata è compresa tra 600 e 700 pixel, anche se è necessario ridimensionare le dimensioni se si tratta di una schermata densa o di una frazione di uno screenshot, rispettivamente.

>[!IMPORTANT]
>È possibile caricare immagini nel repository con fork solo prima dell'Unione. Se quindi si prevede di aggiungere immagini a un articolo, è necessario [usare Visual Studio Code](#using-visual-studio-code) per aggiungere prima le immagini alla cartella "immagini" del fork oppure verificare di aver eseguito quanto segue in un Web browser:
>
>1. Biforcare il repository di MicrosoftDocs/realtà mista.
>2. Modificare l'articolo nel fork.
>3. Le immagini a cui si fa riferimento nell'articolo sono state caricate nella cartella "mixed-Real-docs/images" nel fork.
>4. Creazione di una **richiesta pull** per unire il fork al ramo ' Master ' di MicrosoftDocs/Mixed Reality.
>
>Per informazioni su come configurare un repository con fork, seguire le istruzioni per la [creazione di un nuovo articolo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Visualizzazione in anteprima del lavoro

Durante la modifica in GitHub tramite un Web browser, è possibile fare clic sulla scheda **Anteprima** nella parte superiore della pagina per visualizzare l'anteprima del lavoro prima del commit. 

>[!NOTE]
>L'anteprima delle modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft

Dipendenti Microsoft: una volta che i contributi sono Stati Uniti nel ramo ' Master ', è possibile visualizzare l'aspetto della documentazione prima che diventi pubblico https://review.docs.microsoft.com/windows/mixed-reality?branch=master (trovare l'articolo usando il sommario nella colonna a sinistra).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Modifica nel browser rispetto alla modifica con un client desktop

La modifica nel browser rappresenta il modo più semplice per apportare modifiche rapide, tuttavia, esistono alcuni svantaggi:

- Non si ottiene il controllo ortografico.
- Non si ottiene alcun collegamento intelligente ad altri articoli (è necessario digitare manualmente il nome file dell'articolo).
- Può trattarsi di un problema per caricare le immagini e farvi riferimento.

Se si preferisce non gestire questi problemi, è consigliabile usare un client desktop come [Visual Studio Code](https://code.visualstudio.com/) con un paio di [estensioni utili](#useful-extensions) per contribuire alla documentazione.

## <a name="using-visual-studio-code"></a>Utilizzo di Visual Studio Code

Per i motivi elencati in [precedenza](#editing-in-the-browser-vs-editing-with-a-desktop-client), è preferibile usare un client desktop per modificare la documentazione anziché un Web browser. Si consiglia di usare [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configurazione

Per configurare Visual Studio Code per l'uso con questo repository, seguire questa procedura:

1. In un Web browser:
    1. Installare [git per il PC](https://git-scm.com/downloads).
    2. Installare [Visual Studio Code](https://code.visualstudio.com/).
    3. [MicrosoftDocs di divisione/realtà mista,](#creating-a-new-article) se non è già stato fatto.
    4. Nel fork fare clic su **clona o Scarica** e copiare l'URL.
2. Creare un clone locale del fork in Visual Studio Code:
    1. Scegliere **riquadro comandi**dal menu **Visualizza** .
    2. Digitare "git: clone".
    3. Incollare l'URL appena copiato.
    4. Scegliere la posizione in cui salvare il clone nel PC.
    5. Nella finestra popup fare clic su **Apri repository** .

### <a name="editing-documentation"></a>Modifica della documentazione

Usare il flusso di lavoro seguente per apportare modifiche alla documentazione con Visual Studio Code:

>[!NOTE]
>Tutte le linee guida per la [modifica](#editing-an-existing-article) e la [creazione](#creating-a-new-article) di articoli e le nozioni [di base per la modifica di Markdown](#markdown-basics)vengono applicate anche quando si usa Visual Studio Code.

1. Verificare che il fork clonato sia aggiornato con il repository ufficiale.
   1. In un Web browser creare una richiesta pull per sincronizzare le modifiche recenti da altri collaboratori in MicrosoftDocs/Mixed-Reality ' Master ' al fork (assicurarsi che la freccia indichi il modo corretto).
      
      ![Sincronizza le modifiche da MicrosoftDocs/Mixed-Reality al fork](images/sync_repos.PNG)
   2. In Visual Studio Code fare clic sul pulsante Sincronizza per sincronizzare il fork aggiornato al momento del clone locale.
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_clone.png)
2. Creare o modificare gli articoli nel repository clonato usando Visual Studio Code.
   1. Modificare uno o più articoli (aggiungere immagini alla cartella "immagini", se necessario).
   2. **Salva** le modifiche in **Esplora**.
      
      ![Scegliere "Salva tutto" in Esplora risorse](images/explorer_save.png)
   3. Esegui il **commit di tutte** le modifiche nel **controllo del codice sorgente** (Scrivi messaggio di commit quando richiesto).
      
      ![Scegliere "Esegui commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. Fare clic sul pulsante **Sincronizza** per sincronizzare le modifiche con l'origine (il fork in GitHub).
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_back.png)
3. In un Web browser creare una richiesta pull per sincronizzare le nuove modifiche nel fork con MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi il modo corretto).

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Estensioni utili

Le estensioni Visual Studio Code seguenti sono molto utili quando si modifica la documentazione:

- [Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : usare **ALT + M** per visualizzare un menu di opzioni di creazione di documenti, ad esempio:
   - Eseguire ricerche e fare riferimento alle immagini caricate.
   - Aggiungere la formattazione, ad esempio elenchi, tabelle e chiamate specifiche di docs come `>[!NOTE]`.
   - Cerca e fa riferimento a collegamenti e segnalibri interni (collegamenti a sezioni specifiche all'interno di una pagina).
   - Gli errori di formattazione sono evidenziati (posizionare il puntatore del mouse sull'errore per altre informazioni).
- [Controllo ortografico codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.
