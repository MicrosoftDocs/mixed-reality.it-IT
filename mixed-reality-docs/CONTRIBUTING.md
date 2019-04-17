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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="cd60d-103">Aggiunta come contributo alla documentazione per sviluppatori di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="cd60d-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="cd60d-104">Ecco il [repository pubblico per la documentazione per sviluppatori di realtà mista di Windows](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="cd60d-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="cd60d-105">Tutti gli articoli vengono create o modificate in questo repository **sarà visibile al pubblico.**</span><span class="sxs-lookup"><span data-stu-id="cd60d-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="cd60d-106">Documentazione della realtà mista di Windows è ora nella piattaforma docs.microsoft.com, che usa GitHub flavored Markdown (con funzionalità Markdig).</span><span class="sxs-lookup"><span data-stu-id="cd60d-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="cd60d-107">In pratica, il contenuto di questo repository è modificare Ottiene trasformato in pagine con stili e formattate che vengano visualizzati nella https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="cd60d-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="cd60d-108">Questa pagina vengono illustrati i passaggi di base e linee guida per contribuire, nonché collegamenti agli elementi di base di Markdown.</span><span class="sxs-lookup"><span data-stu-id="cd60d-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="cd60d-109">Grazie per aver contributo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="cd60d-110">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="cd60d-110">Before you start</span></span>

<span data-ttu-id="cd60d-111">Se non si ha già uno, dovrai [creare un account GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="cd60d-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="cd60d-112">Se si è dipendenti Microsoft, collegare l'account GitHub per l'alias Microsoft sul [portale di Microsoft Open Source](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="cd60d-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="cd60d-113">Aggiungere il **"Microsoft"** e **"MicrosoftDocs"** organizzazioni).</span><span class="sxs-lookup"><span data-stu-id="cd60d-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="cd60d-114">Quando si configura l'account GitHub, è consigliabile anche queste precauzioni di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="cd60d-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="cd60d-115">Creare un [password complessa per l'account Github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="cd60d-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="cd60d-116">Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="cd60d-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="cd60d-117">Salvare il [codici di recupero](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="cd60d-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="cd60d-118">Aggiornamento di [impostazioni del profilo pubblico](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="cd60d-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="cd60d-119">Impostare il nome, quindi è consigliabile impostare il *posta elettronica pubblico* al *non visualizzare l'indirizzo di posta elettronica*.</span><span class="sxs-lookup"><span data-stu-id="cd60d-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="cd60d-120">È consigliabile per caricare foto del profilo, come un'immagine di anteprima verranno visualizzati nelle pagine di docs a cui si contribuisce.</span><span class="sxs-lookup"><span data-stu-id="cd60d-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="cd60d-121">Se si prevede di usare un flusso di lavoro della riga di comando, è consigliabile impostare [Git Credential Manager per Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) in modo che non è necessario immettere la password ogni volta che un contributo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="cd60d-122">Eseguire questi passaggi è importante, in quanto il sistema di pubblicazione è correlato a GitHub e credenziali verrà indicato come autore o collaboratore per ogni articolo che utilizza l'alias di GitHub.</span><span class="sxs-lookup"><span data-stu-id="cd60d-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="cd60d-123">Modifica di un articolo esistente</span><span class="sxs-lookup"><span data-stu-id="cd60d-123">Editing an existing article</span></span>

<span data-ttu-id="cd60d-124">Usare il flusso di lavoro seguente per eseguire gli aggiornamenti per *un articolo esistente* tramite GitHub in un web browser:</span><span class="sxs-lookup"><span data-stu-id="cd60d-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="cd60d-125">Passare all'articolo da modificare nella cartella "mista-realtà-docs".</span><span class="sxs-lookup"><span data-stu-id="cd60d-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="cd60d-126">Selezionare il pulsante Modifica (icona a forma di matita) in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="cd60d-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="cd60d-127">Ciò devierà automaticamente un ramo disposable sul branch 'master'.</span><span class="sxs-lookup"><span data-stu-id="cd60d-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Modifica di un articolo.](images/editpage.png)
3. <span data-ttu-id="cd60d-129">Modificare il contenuto dell'articolo (vedere ["Nozioni di base di Markdown"](#markdown-basics) seguito per informazioni aggiuntive).</span><span class="sxs-lookup"><span data-stu-id="cd60d-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="cd60d-130">Aggiornare i metadati come pertinenti nella parte superiore di ogni articolo:</span><span class="sxs-lookup"><span data-stu-id="cd60d-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="cd60d-131">titolo: Questo è il titolo della pagina visualizzato nella scheda del browser quando viene visualizzato l'articolo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="cd60d-132">Perché viene usata per SEO e indicizzazione, è consigliabile non modificare il titolo a meno che non necessari (anche se questo è meno importante prima di documentazione va pubblica).</span><span class="sxs-lookup"><span data-stu-id="cd60d-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="cd60d-133">Descrizione: Scrivere una breve descrizione del contenuto dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="cd60d-134">Questa procedura favorisce SEO e l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="cd60d-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="cd60d-135">Autore: Se sei il proprietario primario della pagina, aggiungere qui il proprio alias di GitHub.</span><span class="sxs-lookup"><span data-stu-id="cd60d-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="cd60d-136">ms.author: Se sei il proprietario primario della pagina, aggiungere l'alias seguito Microsoft (non occorre @microsoft.com, semplicemente l'alias).</span><span class="sxs-lookup"><span data-stu-id="cd60d-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="cd60d-137">ms.date: Aggiorna la data, se si è aggiunta di contenuto principale alla pagina, ma non per gli aggiornamenti, ad esempio chiarimenti, formattazione, grammatica, o ortografia.</span><span class="sxs-lookup"><span data-stu-id="cd60d-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="cd60d-138">parole chiave: Parole chiave aiutano a SEO (Ottimizzazione motore di ricerca).</span><span class="sxs-lookup"><span data-stu-id="cd60d-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="cd60d-139">Aggiungere le parole chiave, separate da una virgola e uno spazio, che sono specifiche dell'articolo, ma senza punteggiatura dopo l'ultima parola chiave nell'elenco, non devi aggiungere parole chiave globali che si applicano a tutti gli articoli, come quelli gestiti in un' posizione.</span><span class="sxs-lookup"><span data-stu-id="cd60d-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="cd60d-140">Dopo aver completato le modifiche all'articolo, scorrere verso il basso e fare clic sui **Proponi modifica file** pulsante.</span><span class="sxs-lookup"><span data-stu-id="cd60d-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="cd60d-141">Nella pagina successiva, fare clic su **Crea richiesta pull** per unire il ramo creato automaticamente nel 'master'.</span><span class="sxs-lookup"><span data-stu-id="cd60d-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="cd60d-142">Ripetere i passaggi precedenti per il prossimo articolo da modificare.</span><span class="sxs-lookup"><span data-stu-id="cd60d-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="cd60d-143">Creazione di un nuovo articolo</span><span class="sxs-lookup"><span data-stu-id="cd60d-143">Creating a new article</span></span>

<span data-ttu-id="cd60d-144">Usare il seguente flusso di lavoro *creare un nuovo articolo* in tramite GitHub del repository della documentazione in un web browser:</span><span class="sxs-lookup"><span data-stu-id="cd60d-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="cd60d-145">Creare un fork al ramo 'master' MicrosoftDocs/realtà mista (usando il **Fork** pulsante in alto a destra).</span><span class="sxs-lookup"><span data-stu-id="cd60d-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Fork al ramo master.](images/forkbranch.png)
2. <span data-ttu-id="cd60d-147">Nella cartella "mista-realtà-docs", fare clic sui **Crea nuovo file** pulsante in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="cd60d-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="cd60d-148">Creare un nome di pagina per l'articolo (utilizzare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere "MD"</span><span class="sxs-lookup"><span data-stu-id="cd60d-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Denominare la nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="cd60d-150">Assicurarsi di che creare il nuovo articolo all'interno della cartella "mista-realtà-docs".</span><span class="sxs-lookup"><span data-stu-id="cd60d-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="cd60d-151">È possibile verificarlo controllando per "/ documentazione di realtà mista /" nella riga del nome file nuovo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="cd60d-152">Nella parte superiore della pagina di nuovo, aggiungere il seguente blocco di metadati:</span><span class="sxs-lookup"><span data-stu-id="cd60d-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="cd60d-153">Compilare i campi di metadati pertinenti per le istruzioni riportate nel [sezione precedente](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="cd60d-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="cd60d-154">Scrittura articolo contenuto mediante [nozioni di base di Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="cd60d-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="cd60d-155">Aggiungere un `## See also` nella parte inferiore dell'articolo con collegamenti ad altri articoli pertinenti.</span><span class="sxs-lookup"><span data-stu-id="cd60d-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="cd60d-156">Al termine, fare clic su **file nuovo Commit**.</span><span class="sxs-lookup"><span data-stu-id="cd60d-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="cd60d-157">Fare clic su **nuova richiesta pull** e unire il ramo 'master' del fork in MicrosoftDocs/realtà mista 'master' (assicurarsi che la freccia indica il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="cd60d-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Crea richiesta pull dal fork in MicrosoftDocs/realtà mista](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="cd60d-159">Nozioni di base di markdown</span><span class="sxs-lookup"><span data-stu-id="cd60d-159">Markdown basics</span></span>

<span data-ttu-id="cd60d-160">Le risorse seguenti consentono di imparare a modificare documentazione usando il linguaggio Markdown:</span><span class="sxs-lookup"><span data-stu-id="cd60d-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="cd60d-161">Nozioni di base di markdown</span><span class="sxs-lookup"><span data-stu-id="cd60d-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="cd60d-162">Poster di riferimento markdown nella-panoramica</span><span class="sxs-lookup"><span data-stu-id="cd60d-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="cd60d-163">Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="cd60d-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="cd60d-164">Aggiunta di tabelle</span><span class="sxs-lookup"><span data-stu-id="cd60d-164">Adding tables</span></span>

<span data-ttu-id="cd60d-165">A causa di tabelle, gli stili modo docs.microsoft.com non avranno bordi o stili personalizzati, anche se si tenta di CSS in linea.</span><span class="sxs-lookup"><span data-stu-id="cd60d-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="cd60d-166">Sembrerà funzionare per un breve periodo di tempo, ma alla fine della piattaforma verrà cancellati lo stile fuori dalla tabella.</span><span class="sxs-lookup"><span data-stu-id="cd60d-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="cd60d-167">Pertanto, pianificare in anticipo e mantenere le tabelle semplici.</span><span class="sxs-lookup"><span data-stu-id="cd60d-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="cd60d-168">[Di seguito è un sito che semplifica le tabelle Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="cd60d-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="cd60d-169">Il [estensione Docs Markdown per Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) inoltre rende tabella generazione facile se si usa [Visual Studio Code (vedere sotto)](#using-visual-studio-code) per modificare la documentazione.</span><span class="sxs-lookup"><span data-stu-id="cd60d-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="cd60d-170">Aggiunta di immagini</span><span class="sxs-lookup"><span data-stu-id="cd60d-170">Adding images</span></span>

<span data-ttu-id="cd60d-171">È necessario caricare le immagini nella cartella "mista-realtà-docs/immagini" nel repository e quindi farvi riferimento in modo appropriato nell'articolo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="cd60d-172">Le immagini verranno automaticamente visualizzati a dimensioni intere, che indica se l'immagine è grande, verrà inserito l'intera larghezza dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="cd60d-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="cd60d-173">In questo modo, si consiglia di pre-ridimensionamento delle immagini prima di caricarli.</span><span class="sxs-lookup"><span data-stu-id="cd60d-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="cd60d-174">La larghezza consigliata è compreso tra 600 e 700 pixel, se si deve ridimensionare verso l'alto o verso il basso se è una schermata di tipo densa o una frazione di una schermata, rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="cd60d-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="cd60d-175">È possibile caricare le immagini solo per il repository con fork prima dell'unione.</span><span class="sxs-lookup"><span data-stu-id="cd60d-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="cd60d-176">Pertanto, se si prevede di aggiungere immagini a un articolo, dovrai [usare Visual Studio Code](#using-visual-studio-code) innanzitutto aggiungere le immagini nella cartella "images" del fork o assicurarsi di aver eseguito le operazioni seguenti in un web browser:</span><span class="sxs-lookup"><span data-stu-id="cd60d-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="cd60d-177">Duplicato il repository di MicrosoftDocs/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cd60d-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="cd60d-178">Modificare l'articolo nel fork.</span><span class="sxs-lookup"><span data-stu-id="cd60d-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="cd60d-179">Caricare le immagini di che cui si fa riferimento nell'articolo nella cartella "mista-realtà-docs/immagini" nel fork.</span><span class="sxs-lookup"><span data-stu-id="cd60d-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="cd60d-180">Creato un **richiesta pull** nel fork di tipo merge nel ramo 'master' MicrosoftDocs/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cd60d-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="cd60d-181">Per informazioni su come impostare il repository con fork, seguire le istruzioni relative [creando un nuovo articolo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="cd60d-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="cd60d-182">La visualizzazione in anteprima il lavoro</span><span class="sxs-lookup"><span data-stu-id="cd60d-182">Previewing your work</span></span>

<span data-ttu-id="cd60d-183">Quando si modifica in GitHub tramite un web browser, è possibile scegliere il **Preview** scheda nella parte superiore della pagina per visualizzare in anteprima il lavoro prima di eseguire il commit.</span><span class="sxs-lookup"><span data-stu-id="cd60d-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="cd60d-184">La visualizzazione in anteprima le modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft</span><span class="sxs-lookup"><span data-stu-id="cd60d-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="cd60d-185">I dipendenti Microsoft: una volta che i tuoi contributi sono stati uniti nel ramo 'master', è possibile visualizzare la documentazione di aspetto prima che diventi pubblico in https://review.docs.microsoft.com/windows/mixed-reality?branch=master (trovare l'articolo utilizzando il sommario nella colonna sinistra).</span><span class="sxs-lookup"><span data-stu-id="cd60d-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="cd60d-186">Modifica il browser o di modifica con un client desktop</span><span class="sxs-lookup"><span data-stu-id="cd60d-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="cd60d-187">La modifica nel browser è il modo più semplice per apportare modifiche rapide, esistono tuttavia alcuni svantaggi:</span><span class="sxs-lookup"><span data-stu-id="cd60d-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="cd60d-188">Non si ottiene il controllo ortografico.</span><span class="sxs-lookup"><span data-stu-id="cd60d-188">You don't get spell-check.</span></span>
- <span data-ttu-id="cd60d-189">Non si ottiene alcun collegamento smart ad altri articoli (è necessario digitare manualmente il nome dell'articolo).</span><span class="sxs-lookup"><span data-stu-id="cd60d-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="cd60d-190">Può essere una seccatura di caricare e fare riferimento a immagini.</span><span class="sxs-lookup"><span data-stu-id="cd60d-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="cd60d-191">Se invece potrebbe non risolvere questi problemi, è preferibile usare un client desktop, ad esempio [Visual Studio Code](https://code.visualstudio.com/) con un paio [estensioni utili](#useful-extensions) contribuire alla documentazione.</span><span class="sxs-lookup"><span data-stu-id="cd60d-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="cd60d-192">Uso di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cd60d-192">Using Visual Studio Code</span></span>

<span data-ttu-id="cd60d-193">Per i motivi elencati [sopra](#editing-in-the-browser-vs-editing-with-a-desktop-client), potrebbe essere preferibile utilizzando un client desktop per modificare la documentazione anziché un web browser.</span><span class="sxs-lookup"><span data-stu-id="cd60d-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="cd60d-194">È consigliabile usare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="cd60d-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="cd60d-195">Configurazione</span><span class="sxs-lookup"><span data-stu-id="cd60d-195">Setup</span></span>

<span data-ttu-id="cd60d-196">Seguire questi passaggi per configurare Visual Studio Code per lavorare con questo repository:</span><span class="sxs-lookup"><span data-stu-id="cd60d-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="cd60d-197">In un web browser:</span><span class="sxs-lookup"><span data-stu-id="cd60d-197">In a web browser:</span></span>
    1. <span data-ttu-id="cd60d-198">Installare [Git per il PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="cd60d-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="cd60d-199">Installare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="cd60d-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="cd60d-200">[Creare la biforcazione MicrosoftDocs/realtà mista](#creating-a-new-article) se hai già fatto.</span><span class="sxs-lookup"><span data-stu-id="cd60d-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="cd60d-201">Nel fork, fare clic su **Clona o Scarica** e copiare l'URL.</span><span class="sxs-lookup"><span data-stu-id="cd60d-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="cd60d-202">Creare un clone della fork locale in Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="cd60d-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="cd60d-203">Dal **View** dal menu **comandi**.</span><span class="sxs-lookup"><span data-stu-id="cd60d-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="cd60d-204">Tipo "Git:Clone."</span><span class="sxs-lookup"><span data-stu-id="cd60d-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="cd60d-205">Incollare l'URL appena copiato.</span><span class="sxs-lookup"><span data-stu-id="cd60d-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="cd60d-206">Specificare dove salvare il clone nel PC.</span><span class="sxs-lookup"><span data-stu-id="cd60d-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="cd60d-207">Fare clic su **repository Open** nella finestra popup.</span><span class="sxs-lookup"><span data-stu-id="cd60d-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="cd60d-208">Documentazione di modifica</span><span class="sxs-lookup"><span data-stu-id="cd60d-208">Editing documentation</span></span>

<span data-ttu-id="cd60d-209">Per apportare modifiche alla documentazione di Visual Studio code, usare il flusso di lavoro seguente:</span><span class="sxs-lookup"><span data-stu-id="cd60d-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="cd60d-210">Tutto il materiale sussidiario per [editing](#editing-an-existing-article) e [creazione](#creating-a-new-article) articoli e il [nozioni di base della modifica di Markdown](#markdown-basics), dall'esempio precedente si applica quando si usa anche Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cd60d-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="cd60d-211">Assicurarsi che sia aggiornato con il repository ufficiale nel fork clonato.</span><span class="sxs-lookup"><span data-stu-id="cd60d-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="cd60d-212">In un web browser, creare una richiesta pull per sincronizzare le modifiche recenti di altri collaboratori in MicrosoftDocs/realtà mista "master" nel fork (assicurarsi che la freccia indica il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="cd60d-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizzare le modifiche da MicrosoftDocs/realtà mista al fork](images/sync_repos.PNG)
   2. <span data-ttu-id="cd60d-214">In Visual Studio Code fare clic sul pulsante di sincronizzazione per sincronizzare il fork appena aggiornato al clone locale.</span><span class="sxs-lookup"><span data-stu-id="cd60d-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Fare clic sul pulsante di sincronizzazione](images/sync_clone.png)
2. <span data-ttu-id="cd60d-216">Creare o modificare articoli nel repository clonato usando Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cd60d-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="cd60d-217">Modificare uno o più articoli (aggiungere immagini nella cartella "images" se necessario).</span><span class="sxs-lookup"><span data-stu-id="cd60d-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="cd60d-218">**Salvare** Cambia **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="cd60d-218">**Save** changes in **Explorer**.</span></span>
      
      ![Scegliere "Salva tutte le" in Esplora](images/explorer_save.png)
   3. <span data-ttu-id="cd60d-220">**Esegui commit di tutto** Cambia **controllo del codice sorgente** (messaggio di commit quando viene richiesto di scrittura).</span><span class="sxs-lookup"><span data-stu-id="cd60d-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Scegliere "Esegui Commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. <span data-ttu-id="cd60d-222">Scegliere il **sincronizzazione** pulsante per sincronizzare le modifiche all'origine (il fork su GitHub).</span><span class="sxs-lookup"><span data-stu-id="cd60d-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Fare clic sul pulsante di sincronizzazione](images/sync_back.png)
3. <span data-ttu-id="cd60d-224">In un web browser, creare una richiesta pull per sincronizzare le nuove modifiche nel fork al MicrosoftDocs/realtà mista 'master' (assicurarsi che la freccia indica il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="cd60d-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Crea richiesta pull dal fork in MicrosoftDocs/realtà mista](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="cd60d-226">Estensioni utili</span><span class="sxs-lookup"><span data-stu-id="cd60d-226">Useful extensions</span></span>

<span data-ttu-id="cd60d-227">Le seguenti estensioni di Visual Studio Code sono molto utili quando si modifica la documentazione:</span><span class="sxs-lookup"><span data-stu-id="cd60d-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="cd60d-228">[Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -utilizzare **Alt + M** per visualizzare un menu di docs authoring opzioni, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="cd60d-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="cd60d-229">Ricerca e riferimento immagini caricate.</span><span class="sxs-lookup"><span data-stu-id="cd60d-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="cd60d-230">Aggiungere la formattazione, ad esempio elenchi, tabelle e callout specifiche di docs, ad esempio `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="cd60d-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="cd60d-231">Eseguire la ricerca e fare riferimento i collegamenti interni e ai segnalibri (collegamenti a sezioni specifiche all'interno di una pagina).</span><span class="sxs-lookup"><span data-stu-id="cd60d-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="cd60d-232">Errori di formattazione vengono evidenziati (posizionare il mouse sopra l'errore per ulteriori informazioni).</span><span class="sxs-lookup"><span data-stu-id="cd60d-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="cd60d-233">[Controllo ortografico di codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -parole errate verrà sottolineate; fare clic su una parola errata per modificarla o salvarlo al dizionario.</span><span class="sxs-lookup"><span data-stu-id="cd60d-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
