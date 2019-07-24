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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="1be73-103">Contributo alla documentazione per gli sviluppatori di Microsoft Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1be73-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="1be73-104">Il [repository pubblico per la documentazione per gli sviluppatori di Microsoft Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)</span><span class="sxs-lookup"><span data-stu-id="1be73-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="1be73-105">Eventuali articoli creati o modificati in questo repository **saranno visibili al pubblico.**</span><span class="sxs-lookup"><span data-stu-id="1be73-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="1be73-106">I documenti di realtà mista di Windows sono ora disponibili nella piattaforma docs.microsoft.com, che usa Markdown di GitHub (con le funzionalità di Markdig).</span><span class="sxs-lookup"><span data-stu-id="1be73-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="1be73-107">In pratica, il contenuto modificato in questo repository viene trasformato in pagine formattate e stilizzate visualizzate https://docs.microsoft.com/windows/mixed-reality in.</span><span class="sxs-lookup"><span data-stu-id="1be73-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="1be73-108">In questa pagina vengono illustrati i passaggi e le linee guida di base per i contributi, oltre a collegamenti alle nozioni di base di Markdown.</span><span class="sxs-lookup"><span data-stu-id="1be73-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="1be73-109">Grazie per il contributo.</span><span class="sxs-lookup"><span data-stu-id="1be73-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1be73-110">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="1be73-110">Before you start</span></span>

<span data-ttu-id="1be73-111">Se non si ha già un account, è necessario [creare un account github](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="1be73-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="1be73-112">Se si è un dipendente Microsoft, collegare il proprio account GitHub al proprio alias Microsoft nel [portale Open source Microsoft](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="1be73-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="1be73-113">Unisciti alle organizzazioni **"Microsoft"** e **"MicrosoftDocs"** .</span><span class="sxs-lookup"><span data-stu-id="1be73-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="1be73-114">Quando si configura l'account GitHub, si consigliano anche le precauzioni di sicurezza seguenti:</span><span class="sxs-lookup"><span data-stu-id="1be73-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="1be73-115">Creare una [password complessa per l'account github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="1be73-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="1be73-116">Abilitare [l'autenticazione a due fattori](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="1be73-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="1be73-117">Salvare i [codici di ripristino](https://github.com/settings/auth/recovery-codes) in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="1be73-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="1be73-118">Aggiornare le [impostazioni del profilo pubblico](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="1be73-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="1be73-119">Impostare il nome e prendere in considerazione l'impostazione del *messaggio di posta elettronica pubblico* in modo che *non venga visualizzato l'indirizzo di posta elettronica*</span><span class="sxs-lookup"><span data-stu-id="1be73-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="1be73-120">Si consiglia di caricare un'immagine del profilo, in quanto verrà visualizzata un'anteprima nelle pagine di docs a cui si collabora.</span><span class="sxs-lookup"><span data-stu-id="1be73-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="1be73-121">Se si prevede di usare un flusso di lavoro della riga di comando, è consigliabile impostare [git Credential Manager per Windows in](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) modo da non dover immettere la password ogni volta che si crea un contributo.</span><span class="sxs-lookup"><span data-stu-id="1be73-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="1be73-122">L'esecuzione di questi passaggi è importante, poiché il sistema di pubblicazione è associato a GitHub e verrà elencato come autore o collaboratore per ogni articolo usando l'alias GitHub.</span><span class="sxs-lookup"><span data-stu-id="1be73-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="1be73-123">Modifica di un articolo esistente</span><span class="sxs-lookup"><span data-stu-id="1be73-123">Editing an existing article</span></span>

<span data-ttu-id="1be73-124">Usare il flusso di lavoro seguente per apportare aggiornamenti a *un articolo esistente* tramite GitHub in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="1be73-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1be73-125">Passare all'articolo che si vuole modificare nella cartella "Mixed-Reality-docs".</span><span class="sxs-lookup"><span data-stu-id="1be73-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="1be73-126">Selezionare il pulsante modifica (icona a matita) in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="1be73-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="1be73-127">Verrà automaticamente creato un ramo eliminabile dal ramo ' Master '.</span><span class="sxs-lookup"><span data-stu-id="1be73-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Modificare un articolo.](images/editpage.png)
3. <span data-ttu-id="1be73-129">Modificare il contenuto dell'articolo (vedere ["Nozioni di base di Markdown"](#markdown-basics) di seguito per informazioni aggiuntive).</span><span class="sxs-lookup"><span data-stu-id="1be73-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="1be73-130">Aggiornare i metadati come pertinente all'inizio di ogni articolo:</span><span class="sxs-lookup"><span data-stu-id="1be73-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="1be73-131">titolo Si tratta del titolo della pagina che viene visualizzato nella scheda del browser quando viene visualizzato l'articolo.</span><span class="sxs-lookup"><span data-stu-id="1be73-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="1be73-132">Poiché questa operazione viene usata per l'indicizzazione e l'ottimizzazione, non è necessario modificare il titolo a meno che non sia necessario (sebbene questo sia meno critico prima che la documentazione diventi pubblica).</span><span class="sxs-lookup"><span data-stu-id="1be73-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="1be73-133">Descrizione Scrivere una breve descrizione del contenuto dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="1be73-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="1be73-134">Questa operazione favorisce la SEO e l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="1be73-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="1be73-135">autore Se si è il proprietario principale della pagina, aggiungere qui l'alias GitHub.</span><span class="sxs-lookup"><span data-stu-id="1be73-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="1be73-136">ms. Author: Se si è il proprietario principale della pagina, aggiungere qui l'alias Microsoft (non è necessario @microsoft.com, solo l'alias).</span><span class="sxs-lookup"><span data-stu-id="1be73-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="1be73-137">ms. Data: Aggiornare la data se si aggiunge contenuto principale alla pagina, ma non per correzioni quali chiarimenti, formattazione, grammatica o ortografia.</span><span class="sxs-lookup"><span data-stu-id="1be73-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="1be73-138">Parole Parole chiave che facilitano il SEO (ottimizzazione del motore di ricerca).</span><span class="sxs-lookup"><span data-stu-id="1be73-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="1be73-139">Aggiungere parole chiave, separate da una virgola e uno spazio, specifiche dell'articolo (ma senza punteggiatura dopo l'ultima parola chiave nell'elenco); non è necessario aggiungere parole chiave globali che si applicano a tutti gli articoli, perché sono gestite altrove.</span><span class="sxs-lookup"><span data-stu-id="1be73-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="1be73-140">Una volta completate le modifiche apportate all'articolo, scorrere verso il basso e fare clic sul pulsante **Proponi modifica file** .</span><span class="sxs-lookup"><span data-stu-id="1be73-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="1be73-141">Nella pagina successiva fare clic su **Crea richiesta pull** per unire il ramo creato automaticamente in ' Master '.</span><span class="sxs-lookup"><span data-stu-id="1be73-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="1be73-142">Ripetere i passaggi precedenti per il prossimo articolo che si desidera modificare.</span><span class="sxs-lookup"><span data-stu-id="1be73-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="1be73-143">Creazione di un nuovo articolo</span><span class="sxs-lookup"><span data-stu-id="1be73-143">Creating a new article</span></span>

<span data-ttu-id="1be73-144">Usare il flusso di lavoro seguente per *creare nuovi articoli* nel repository della documentazione tramite GitHub in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="1be73-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="1be73-145">Creare un fork dal ramo ' Master ' di MicrosoftDocs/Mixed-Reality (usando il pulsante **fork** in alto a destra).</span><span class="sxs-lookup"><span data-stu-id="1be73-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Creare un fork del ramo master.](images/forkbranch.png)
2. <span data-ttu-id="1be73-147">Nella cartella "Mixed-Reality-docs" fare clic sul pulsante **Crea nuovo file** in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="1be73-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="1be73-148">Creare un nome di pagina per l'articolo (usare i trattini anziché gli spazi e non usare segni di punteggiatura o apostrofi) e aggiungere ". MD"</span><span class="sxs-lookup"><span data-stu-id="1be73-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Assegnare un nome alla nuova pagina.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="1be73-150">Assicurarsi di creare il nuovo articolo dall'interno della cartella "mixed-Real-docs".</span><span class="sxs-lookup"><span data-stu-id="1be73-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="1be73-151">Per confermare questo problema, verificare la presenza di "/Mixed-Reality-docs/" nella nuova riga nome file.</span><span class="sxs-lookup"><span data-stu-id="1be73-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="1be73-152">Nella parte superiore della nuova pagina aggiungere il blocco di metadati seguente:</span><span class="sxs-lookup"><span data-stu-id="1be73-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="1be73-153">Compilare i campi dei metadati pertinenti in base alle istruzioni riportate nella [sezione precedente](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="1be73-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="1be73-154">Scrivere il contenuto dell'articolo usando le [nozioni fondamentali di Markdown](#markdown-basics)</span><span class="sxs-lookup"><span data-stu-id="1be73-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="1be73-155">Aggiungere una `## See also` sezione nella parte inferiore dell'articolo con i collegamenti ad altri articoli pertinenti.</span><span class="sxs-lookup"><span data-stu-id="1be73-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="1be73-156">Al termine, fare clic su Esegui **commit nuovo file**.</span><span class="sxs-lookup"><span data-stu-id="1be73-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="1be73-157">Fare clic su **nuova richiesta pull** e unire il ramo ' Master ' del fork in MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi la modalità corretta).</span><span class="sxs-lookup"><span data-stu-id="1be73-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="1be73-159">Nozioni fondamentali su Markdown</span><span class="sxs-lookup"><span data-stu-id="1be73-159">Markdown basics</span></span>

<span data-ttu-id="1be73-160">Le risorse seguenti consentiranno di apprendere come modificare la documentazione utilizzando il linguaggio markdown:</span><span class="sxs-lookup"><span data-stu-id="1be73-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="1be73-161">Nozioni fondamentali su Markdown</span><span class="sxs-lookup"><span data-stu-id="1be73-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="1be73-162">Poster di riferimento Markdown-at-Glance</span><span class="sxs-lookup"><span data-stu-id="1be73-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="1be73-163">Risorse aggiuntive per la scrittura di Markdown per docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="1be73-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="1be73-164">Aggiunta di tabelle</span><span class="sxs-lookup"><span data-stu-id="1be73-164">Adding tables</span></span>

<span data-ttu-id="1be73-165">A causa del modo in cui le tabelle docs.microsoft.com stili, non avranno bordi o stili personalizzati, anche se si prova a usare CSS inline.</span><span class="sxs-lookup"><span data-stu-id="1be73-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="1be73-166">Sembra funzionare per un breve periodo di tempo, ma alla fine la piattaforma eliminerà lo stile dalla tabella.</span><span class="sxs-lookup"><span data-stu-id="1be73-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="1be73-167">Pianificare in anticipo e semplificare le tabelle.</span><span class="sxs-lookup"><span data-stu-id="1be73-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="1be73-168">[Ecco un sito che semplifica la semplicità delle tabelle Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="1be73-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="1be73-169">L' [estensione docs Markdown per Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) rende inoltre semplice la generazione di tabelle se si usa [Visual Studio Code (vedere di seguito)](#using-visual-studio-code) per modificare la documentazione.</span><span class="sxs-lookup"><span data-stu-id="1be73-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="1be73-170">Aggiunta di immagini</span><span class="sxs-lookup"><span data-stu-id="1be73-170">Adding images</span></span>

<span data-ttu-id="1be73-171">È necessario caricare le immagini nella cartella "mixed-Real-docs/images" del repository e quindi farvi riferimento in modo appropriato nell'articolo.</span><span class="sxs-lookup"><span data-stu-id="1be73-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="1be73-172">Le immagini verranno automaticamente visualizzate a dimensione completa, il che significa che se l'immagine è di grandi dimensioni, riempirà tutta la larghezza dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="1be73-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="1be73-173">È quindi consigliabile pre-dimensionare le immagini prima di caricarle.</span><span class="sxs-lookup"><span data-stu-id="1be73-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="1be73-174">La larghezza consigliata è compresa tra 600 e 700 pixel, anche se è necessario ridimensionare le dimensioni se si tratta di una schermata densa o di una frazione di uno screenshot, rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="1be73-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1be73-175">È possibile caricare immagini nel repository con fork solo prima dell'Unione.</span><span class="sxs-lookup"><span data-stu-id="1be73-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="1be73-176">Se quindi si prevede di aggiungere immagini a un articolo, è necessario [usare Visual Studio Code](#using-visual-studio-code) per aggiungere prima le immagini alla cartella "immagini" del fork oppure verificare di aver eseguito quanto segue in un Web browser:</span><span class="sxs-lookup"><span data-stu-id="1be73-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="1be73-177">Biforcare il repository di MicrosoftDocs/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1be73-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="1be73-178">Modificare l'articolo nel fork.</span><span class="sxs-lookup"><span data-stu-id="1be73-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="1be73-179">Le immagini a cui si fa riferimento nell'articolo sono state caricate nella cartella "mixed-Real-docs/images" nel fork.</span><span class="sxs-lookup"><span data-stu-id="1be73-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="1be73-180">Creazione di una **richiesta pull** per unire il fork al ramo ' Master ' di MicrosoftDocs/Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1be73-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="1be73-181">Per informazioni su come configurare un repository con fork, seguire le istruzioni per la [creazione di un nuovo articolo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="1be73-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="1be73-182">Visualizzazione in anteprima del lavoro</span><span class="sxs-lookup"><span data-stu-id="1be73-182">Previewing your work</span></span>

<span data-ttu-id="1be73-183">Durante la modifica in GitHub tramite un Web browser, è possibile fare clic sulla scheda **Anteprima** nella parte superiore della pagina per visualizzare l'anteprima del lavoro prima del commit.</span><span class="sxs-lookup"><span data-stu-id="1be73-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="1be73-184">L'anteprima delle modifiche in review.docs.microsoft.com è disponibile solo per i dipendenti Microsoft</span><span class="sxs-lookup"><span data-stu-id="1be73-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="1be73-185">Dipendenti Microsoft: una volta che i contributi sono Stati Uniti nel ramo ' Master ', è possibile visualizzare l'aspetto della documentazione prima che diventi pubblico https://review.docs.microsoft.com/windows/mixed-reality?branch=master (trovare l'articolo usando il sommario nella colonna a sinistra).</span><span class="sxs-lookup"><span data-stu-id="1be73-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="1be73-186">Modifica nel browser rispetto alla modifica con un client desktop</span><span class="sxs-lookup"><span data-stu-id="1be73-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="1be73-187">La modifica nel browser rappresenta il modo più semplice per apportare modifiche rapide, tuttavia, esistono alcuni svantaggi:</span><span class="sxs-lookup"><span data-stu-id="1be73-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="1be73-188">Non si ottiene il controllo ortografico.</span><span class="sxs-lookup"><span data-stu-id="1be73-188">You don't get spell-check.</span></span>
- <span data-ttu-id="1be73-189">Non si ottiene alcun collegamento intelligente ad altri articoli (è necessario digitare manualmente il nome file dell'articolo).</span><span class="sxs-lookup"><span data-stu-id="1be73-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="1be73-190">Può trattarsi di un problema per caricare le immagini e farvi riferimento.</span><span class="sxs-lookup"><span data-stu-id="1be73-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="1be73-191">Se si preferisce non gestire questi problemi, è consigliabile usare un client desktop come [Visual Studio Code](https://code.visualstudio.com/) con un paio di [estensioni utili](#useful-extensions) per contribuire alla documentazione.</span><span class="sxs-lookup"><span data-stu-id="1be73-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="1be73-192">Utilizzo di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1be73-192">Using Visual Studio Code</span></span>

<span data-ttu-id="1be73-193">Per i motivi elencati in [precedenza](#editing-in-the-browser-vs-editing-with-a-desktop-client), è preferibile usare un client desktop per modificare la documentazione anziché un Web browser.</span><span class="sxs-lookup"><span data-stu-id="1be73-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="1be73-194">Si consiglia di usare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1be73-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="1be73-195">Configurazione</span><span class="sxs-lookup"><span data-stu-id="1be73-195">Setup</span></span>

<span data-ttu-id="1be73-196">Per configurare Visual Studio Code per l'uso con questo repository, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="1be73-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="1be73-197">In un Web browser:</span><span class="sxs-lookup"><span data-stu-id="1be73-197">In a web browser:</span></span>
    1. <span data-ttu-id="1be73-198">Installare [git per il PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="1be73-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="1be73-199">Installare [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1be73-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="1be73-200">[MicrosoftDocs di divisione/realtà mista,](#creating-a-new-article) se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="1be73-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="1be73-201">Nel fork fare clic su **clona o Scarica** e copiare l'URL.</span><span class="sxs-lookup"><span data-stu-id="1be73-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="1be73-202">Creare un clone locale del fork in Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1be73-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="1be73-203">Scegliere **riquadro comandi**dal menu **Visualizza** .</span><span class="sxs-lookup"><span data-stu-id="1be73-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="1be73-204">Digitare "git: clone".</span><span class="sxs-lookup"><span data-stu-id="1be73-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="1be73-205">Incollare l'URL appena copiato.</span><span class="sxs-lookup"><span data-stu-id="1be73-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="1be73-206">Scegliere la posizione in cui salvare il clone nel PC.</span><span class="sxs-lookup"><span data-stu-id="1be73-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="1be73-207">Nella finestra popup fare clic su **Apri repository** .</span><span class="sxs-lookup"><span data-stu-id="1be73-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="1be73-208">Modifica della documentazione</span><span class="sxs-lookup"><span data-stu-id="1be73-208">Editing documentation</span></span>

<span data-ttu-id="1be73-209">Usare il flusso di lavoro seguente per apportare modifiche alla documentazione con Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1be73-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="1be73-210">Tutte le linee guida per la [modifica](#editing-an-existing-article) e la [creazione](#creating-a-new-article) di articoli e le nozioni [di base per la modifica di Markdown](#markdown-basics)vengono applicate anche quando si usa Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1be73-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="1be73-211">Verificare che il fork clonato sia aggiornato con il repository ufficiale.</span><span class="sxs-lookup"><span data-stu-id="1be73-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="1be73-212">In un Web browser creare una richiesta pull per sincronizzare le modifiche recenti da altri collaboratori in MicrosoftDocs/Mixed-Reality ' Master ' al fork (assicurarsi che la freccia indichi il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="1be73-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizza le modifiche da MicrosoftDocs/Mixed-Reality al fork](images/sync_repos.PNG)
   2. <span data-ttu-id="1be73-214">In Visual Studio Code fare clic sul pulsante Sincronizza per sincronizzare il fork aggiornato al momento del clone locale.</span><span class="sxs-lookup"><span data-stu-id="1be73-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_clone.png)
2. <span data-ttu-id="1be73-216">Creare o modificare gli articoli nel repository clonato usando Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1be73-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="1be73-217">Modificare uno o più articoli (aggiungere immagini alla cartella "immagini", se necessario).</span><span class="sxs-lookup"><span data-stu-id="1be73-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="1be73-218">**Salva** le modifiche in **Esplora**.</span><span class="sxs-lookup"><span data-stu-id="1be73-218">**Save** changes in **Explorer**.</span></span>
      
      ![Scegliere "Salva tutto" in Esplora risorse](images/explorer_save.png)
   3. <span data-ttu-id="1be73-220">Esegui il **commit di tutte** le modifiche nel **controllo del codice sorgente** (Scrivi messaggio di commit quando richiesto).</span><span class="sxs-lookup"><span data-stu-id="1be73-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Scegliere "Esegui commit di tutto" nel controllo del codice sorgente](images/source_control_commit.png)
   4. <span data-ttu-id="1be73-222">Fare clic sul pulsante **Sincronizza** per sincronizzare le modifiche con l'origine (il fork in GitHub).</span><span class="sxs-lookup"><span data-stu-id="1be73-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Fare clic sul pulsante Sincronizza.](images/sync_back.png)
3. <span data-ttu-id="1be73-224">In un Web browser creare una richiesta pull per sincronizzare le nuove modifiche nel fork con MicrosoftDocs/Mixed-Reality ' Master ' (assicurarsi che la freccia indichi il modo corretto).</span><span class="sxs-lookup"><span data-stu-id="1be73-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Creare una richiesta pull dal fork in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="1be73-226">Estensioni utili</span><span class="sxs-lookup"><span data-stu-id="1be73-226">Useful extensions</span></span>

<span data-ttu-id="1be73-227">Le estensioni Visual Studio Code seguenti sono molto utili quando si modifica la documentazione:</span><span class="sxs-lookup"><span data-stu-id="1be73-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="1be73-228">[Estensione docs Markdown per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : usare **ALT + M** per visualizzare un menu di opzioni di creazione di documenti, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="1be73-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="1be73-229">Eseguire ricerche e fare riferimento alle immagini caricate.</span><span class="sxs-lookup"><span data-stu-id="1be73-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="1be73-230">Aggiungere la formattazione, ad esempio elenchi, tabelle e chiamate specifiche di docs come `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="1be73-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="1be73-231">Cerca e fa riferimento a collegamenti e segnalibri interni (collegamenti a sezioni specifiche all'interno di una pagina).</span><span class="sxs-lookup"><span data-stu-id="1be73-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="1be73-232">Gli errori di formattazione sono evidenziati (posizionare il puntatore del mouse sull'errore per altre informazioni).</span><span class="sxs-lookup"><span data-stu-id="1be73-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="1be73-233">[Controllo ortografico codice](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : le parole con ortografia errata verranno sottolineate; fare clic con il pulsante destro del mouse su una parola digitata in modo errato per modificarla o salvarla nel dizionario.</span><span class="sxs-lookup"><span data-stu-id="1be73-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
