---
title: Aggiunta come contributo le istruzioni
description: Come contribuire alla documentazione di realtà mista di Windows.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604650"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Aggiunta come contributo alla documentazione per sviluppatori di realtà mista di Windows

Ecco il [repository pubblico per la documentazione per sviluppatori di realtà mista di Windows](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Tutti gli articoli vengono create o modificate in questo repository **sarà visibile al pubblico.** 

Documentazione della realtà mista di Windows è ora nella piattaforma docs.microsoft.com, che usa GitHub flavored Markdown (con funzionalità Markdig). In pratica, il contenuto di questo repository è modificare Ottiene trasformato in pagine con stili e formattate che vengano visualizzati nella https://docs.microsoft.com/windows/mixed-reality. 

Questa pagina vengono illustrati i passaggi di base e linee guida per contribuire, nonché collegamenti agli elementi di base di Markdown. Grazie per aver contributo.

## <a name="before-you-start"></a>Prima di iniziare

Se non si ha già uno, dovrai [creare un account GitHub](https://github.com/join).

>[!NOTE]
>Se si è dipendenti Microsoft, collegare l'account GitHub per l'alias Microsoft sul [portale di Microsoft Open Source](https://repos.opensource.microsoft.com/). Aggiungere il **"Microsoft"** e **"MicrosoftDocs"** organizzazioni).

Quando si configura l'account GitHub, è consigliabile anche queste precauzioni di sicurezza:
- Creare un [password complessa per l'account Github](https://github.com/settings/admin).
- Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).
- Salvare il [codici di recupero](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.
- Aggiornamento di [impostazioni del profilo pubblico](https://github.com/settings/profile).
   - Impostare il nome, quindi è consigliabile impostare il *posta elettronica pubblico* al *non visualizzare l'indirizzo di posta elettronica*.
   - È consigliabile per caricare foto del profilo, come un'immagine di anteprima verranno visualizzati nelle pagine di docs a cui si contribuisce.
- Se si prevede di usare un flusso di lavoro della riga di comando, è consigliabile impostare [Git Credential Manager per Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) in modo che non è necessario immettere la password ogni volta che un contributo.

Eseguire questi passaggi è importante, in quanto il sistema di pubblicazione è correlato a GitHub e credenziali verrà indicato come autore o collaboratore per ogni articolo che utilizza l'alias di GitHub.

## <a name="editing-an-existing-article"></a>Modifica di un articolo esistente

Usare il flusso di lavoro seguente per eseguire gli aggiornamenti per *un articolo esistente* tramite GitHub in un web browser:

1. Passare all'articolo da modificare nella cartella "mista-realtà-docs".
2. Selezionare il pulsante Modifica (icona a forma di matita) in alto a destra. Ciò devierà automaticamente un ramo disposable sul branch 'master'.

   ![Modifica di un articolo.](images/editpage.png)
3. Modificare il contenuto dell'articolo (vedere ["Nozioni di base di Markdown"](#markdown-basics) seguito per informazioni aggiuntive).
4. Aggiornare i metadati come pertinenti nella parte superiore di ogni articolo:
   * titolo: Questo è il titolo della pagina visualizzato nella scheda del browser quando viene visualizzato l'articolo. Perché viene usata per SEO e indicizzazione, è consigliabile non modificare il titolo a meno che non necessari (anche se questo è meno importante prima di documentazione va pubblica).
   * Descrizione: Scrivere una breve descrizione del contenuto dell'articolo. Questa procedura favorisce SEO e l'individuazione.
   * Autore: Se sei il proprietario primario della pagina, aggiungere qui il proprio alias di GitHub.
   * ms.author: Se sei il proprietario primario della pagina, aggiungere l'alias seguito Microsoft (non occorre @microsoft.com, semplicemente l'alias).
   * ms.date: Aggiorna la data, se si è aggiunta di contenuto principale alla pagina, ma non per gli aggiornamenti, ad esempio chiarimenti, formattazione, grammatica, o ortografia.
   * parole chiave: Parole chiave aiutano a SEO (Ottimizzazione motore di ricerca). Aggiungere le parole chiave, separate da una virgola e uno spazio, che sono specifiche dell'articolo, ma senza punteggiatura dopo l'ultima parola chiave nell'elenco, non devi aggiungere parole chiave globali che si applicano a tutti gli articoli, come quelli gestiti in un' posizione. 
5. Dopo aver completato le modifiche all'articolo, scorrere verso il basso e fare clic sui **Proponi modifica file** pulsante.
6. Nella pagina successiva, fare clic su **Crea richiesta pull** per unire il ramo creato automaticamente nel 'master'.
7. Ripetere i passaggi precedenti per il prossimo articolo da modificare.

## <a name="creating-a-new-article"></a>Creazione di un nuovo articolo

Usare il seguente flusso di lavoro *creare un nuovo articolo* in tramite GitHub del repository della documentazione in un web browser:

1. Creare un fork al ramo 'master' MicrosoftDocs/realtà mista (usando il **Fork** pulsante in alto a destra).

   ![Fork al ramo master.](images/forkbranch.png)
2. Nella cartella "mista-realtà-docs", fare clic sui **Crea nuovo file** pulsante in alto a destra.
3. Creare un nome di pagina per l'articolo (utilizzare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere "MD"

   ![Denominare la nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Assicurarsi di che creare il nuovo articolo all'interno della cartella "mista-realtà-docs". È possibile verificarlo controllando per "/ documentazione di realtà mista /" nella riga del nome file nuovo.

4. Nella parte superiore della pagina di nuovo, aggiungere il seguente blocco di metadati:

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

5. Compilare i campi di metadati pertinenti per le istruzioni riportate nel [sezione precedente](#editing-an-existing-article).
6. Scrittura articolo contenuto mediante [nozioni di base di Markdown](#markdown-basics).
7. Aggiungere un `## See also` nella parte inferiore dell'articolo con collegamenti ad altri articoli pertinenti.
8. Al termine, fare clic su **file nuovo Commit**.
9. Fare clic su **nuova richiesta pull** e unire il ramo 'master' del fork in MicrosoftDocs/realtà mista 'master' (assicurarsi che la freccia indica il modo corretto).

   ![Crea richiesta pull dal fork in MicrosoftDocs/realtà mista](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Nozioni di base di markdown

Le risorse seguenti consentono di imparare a modificare documentazione usando il linguaggio Markdown:

- [Nozioni di base di markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Poster di riferimento markdown nella-panoramica](images/MarkdownPoster.pdf)
- [Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Aggiunta di tabelle

A causa di tabelle, gli stili modo docs.microsoft.com non avranno bordi o stili personalizzati, anche se si tenta di CSS in linea. Sembrerà funzionare per un breve periodo di tempo, ma alla fine della piattaforma verrà cancellati lo stile fuori dalla tabella. Pertanto, pianificare in anticipo e mantenere le tabelle semplici. [Di seguito è un sito che semplifica le tabelle Markdown](http://www.tablesgenerator.com/markdown_tables).

Il [estensione Docs Markdown per Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) inoltre rende tabella generazione facile se si usa [Visual Studio Code (vedere sotto)](#using-visual-studio-code) per modificare la documentazione.

### <a name="adding-images"></a>Aggiunta di immagini

È necessario caricare le immagini nella cartella "mista-realtà-docs/immagini" nel repository e quindi farvi riferimento in modo appropriato nell'articolo. Le immagini verranno automaticamente visualizzati a dimensioni intere, che indica se l'immagine è grande, verrà inserito l'intera larghezza dell'articolo. In questo modo, si consiglia di pre-ridimensionamento delle immagini prima di caricarli. La larghezza consigliata è compreso tra 600 e 700 pixel, se si deve ridimensionare verso l'alto o verso il basso se è una schermata di tipo densa o una frazione di una schermata, rispettivamente.

>[!IMPORTANT]
>È possibile caricare le immagini solo per il repository con fork prima dell'unione. Pertanto, se si prevede di aggiungere immagini a un articolo, dovrai [usare Visual Studio Code](#using-visual-studio-code) innanzitutto aggiungere le immagini nella cartella "images" del fork o assicurarsi di aver eseguito le operazioni seguenti in un web browser:
>
>1. Duplicato il repository di MicrosoftDocs/realtà mista.
>2. Modificare l'articolo nel fork.
>3. Caricare le immagini di che cui si fa riferimento nell'articolo nella cartella "mista-realtà-docs/immagini" nel fork.
>4. Creato un **richiesta pull** nel fork di tipo merge nel ramo 'master' MicrosoftDocs/realtà mista.
>
>Per informazioni su come impostare il repository con fork, seguire le istruzioni relative [creando un nuovo articolo](#creating-a-new-article).

## <a name="previewing-your-work"></a>La visualizzazione in anteprima il lavoro

Quando si modifica in GitHub tramite un web browser, è possibile scegliere il **Preview** scheda nella parte superiore della pagina per visualizzare in anteprima il lavoro prima di eseguire il commit. 

>[!NOTE]
>La visualizzazione in anteprima le modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft

I dipendenti Microsoft: una volta che i tuoi contributi sono stati uniti nel ramo 'master', è possibile visualizzare la documentazione di aspetto prima che diventi pubblico in https://review.docs.microsoft.com/windows/mixed-reality?branch=master (trovare l'articolo utilizzando il sommario nella colonna sinistra).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Modifica il browser o di modifica con un client desktop

La modifica nel browser è il modo più semplice per apportare modifiche rapide, esistono tuttavia alcuni svantaggi:

- Non si ottiene il controllo ortografico.
- Non si ottiene alcun collegamento smart ad altri articoli (è necessario digitare manualmente il nome dell'articolo).
- Può essere una seccatura di caricare e fare riferimento a immagini.

Se invece potrebbe non risolvere questi problemi, è preferibile usare un client desktop, ad esempio [Visual Studio Code](https://code.visualstudio.com/) con un paio [estensioni utili](#useful-extensions) contribuire alla documentazione.

## <a name="using-visual-studio-code"></a>Uso di Visual Studio Code

Per i motivi elencati [sopra](#editing-in-the-browser-vs-editing-with-a-desktop-client), potrebbe essere preferibile utilizzando un client desktop per modificare la documentazione anziché un web browser. È consigliabile usare [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configurazione

Seguire questi passaggi per configurare Visual Studio Code per lavorare con questo repository:

1. In un web browser:
    1. Installare [Git per il PC](https://git-scm.com/downloads).
    2. Installare [Visual Studio Code](https://code.visualstudio.com/).
    3. [Creare la biforcazione MicrosoftDocs/realtà mista](#creating-a-new-article) se hai già fatto.
    4. Nel fork, fare clic su **Clona o Scarica** e copiare l'URL.
2. Creare un clone della fork locale in Visual Studio Code:
    1. Dal **View** dal menu **comandi**.
    2. Tipo "Git:Clone."
    3. Incollare l'URL appena copiato.
    4. Specificare dove salvare il clone nel PC.
    5. Fare clic su **repository Open** nella finestra popup.

### <a name="editing-documentation"></a>Documentazione di modifica

Per apportare modifiche alla documentazione di Visual Studio code, usare il flusso di lavoro seguente:

>[!NOTE]
>Tutto il materiale sussidiario per [editing](#editing-an-existing-article) e [creazione](#creating-a-new-article) articoli e il [nozioni di base della modifica di Markdown](#markdown-basics), dall'esempio precedente si applica quando si usa anche Visual Studio Code.

1. Assicurarsi che sia aggiornato con il repository ufficiale nel fork clonato.
   1. In un web browser, creare una richiesta pull per sincronizzare le modifiche recenti di altri collaboratori in MicrosoftDocs/realtà mista "master" nel fork (assicurarsi che la freccia indica il modo corretto).
      
      ![Sincronizzare le modifiche da MicrosoftDocs/realtà mista al fork](images/sync_repos.PNG)
   2. In Visual Studio Code fare clic sul pulsante di sincronizzazione per sincronizzare il fork appena aggiornato al clone locale.
      
      ![Fare clic sul pulsante di sincronizzazione](images/sync_clone.png)
2. Creare o modificare articoli nel repository clonato usando Visual Studio Code.
   1. Modificare uno o più articoli (aggiungere immagini nella cartella "images" se necessario).
   2. **Salvare** Cambia **Explorer**.
      
      ![Scegliere "Salva tutte le" in Esplora](images/explorer_save.png)
   3. **Esegui commit di tutto** Cambia **controllo del codice sorgente** (messaggio di commit quando viene richiesto di scrittura).
      
      ![Scegliere "Esegui Commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. Scegliere il **sincronizzazione** pulsante per sincronizzare le modifiche all'origine (il fork su GitHub).
      
      ![Fare clic sul pulsante di sincronizzazione](images/sync_back.png)
3. In un web browser, creare una richiesta pull per sincronizzare le nuove modifiche nel fork al MicrosoftDocs/realtà mista 'master' (assicurarsi che la freccia indica il modo corretto).

   ![Crea richiesta pull dal fork in MicrosoftDocs/realtà mista](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Estensioni utili

Le seguenti estensioni di Visual Studio Code sono molto utili quando si modifica la documentazione:

- [Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -utilizzare **Alt + M** per visualizzare un menu di docs authoring opzioni, ad esempio:
   - Ricerca e riferimento immagini caricate.
   - Aggiungere la formattazione, ad esempio elenchi, tabelle e callout specifiche di docs, ad esempio `>[!NOTE]`.
   - Eseguire la ricerca e fare riferimento i collegamenti interni e ai segnalibri (collegamenti a sezioni specifiche all'interno di una pagina).
   - Errori di formattazione vengono evidenziati (posizionare il mouse sopra l'errore per ulteriori informazioni).
- [Controllo ortografico di codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -parole errate verrà sottolineate; fare clic su una parola errata per modificarla o salvarlo al dizionario.
