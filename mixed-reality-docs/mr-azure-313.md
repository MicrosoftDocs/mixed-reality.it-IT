---
title: MR e Azure 313-servizio hub Internet
description: Completare questo corso per apprendere come implementare il servizio Hub Azure Internet in una macchina virtuale che esegue Ubuntu 16,4 e quindi visualizzare i dati del messaggio usando Microsoft HoloLens o un auricolare immersivo (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, realtà mista, Academy, Edge, Internet delle cose, esercitazione, API, notifiche, funzioni, tabelle, hololens, immersive, VR, Internet delle cose, macchina virtuale, Ubuntu, Python
ms.openlocfilehash: 7f56c7931bb036d14ab3aa9156706b1f6247195c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437970"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR e Azure 313: servizio hub Internet

![risultato del corso](images/AzureLabs-Lab313-00.png)

In questo corso si apprenderà come implementare un **servizio Hub** Internet degli Azure in una macchina virtuale che esegue il sistema operativo Ubuntu 16,4. Un **app per le funzioni di Azure** verrà quindi usato per ricevere messaggi dalla macchina virtuale Ubuntu e archiviare il risultato in un **servizio tabelle di Azure**. Sarà quindi possibile visualizzare questi dati usando **Power bi** su un auricolare Microsoft HoloLens o immersive (VR).

Il contenuto di questo corso *è applicabile* ai dispositivi IOT Edge, ma ai fini di questo corso, l'attenzione si troverà in un ambiente di macchina virtuale, in modo che l'accesso a un dispositivo perimetrale fisico non sia necessario.

Completando questo corso, si apprenderà come:

- Distribuire un **modulo IOT Edge** in una macchina virtuale (Ubuntu 16 OS), che rappresenterà il dispositivo Internet delle cose.
- Aggiungere un **modello Tensorflow di Azure visione personalizzata** al modulo perimetrale, con codice che analizzerà le immagini archiviate nel contenitore.
- Configurare il modulo per inviare di nuovo il messaggio di risultato dell'analisi al **servizio Hub**Internet delle cose.
- Usare un **app per le funzioni di Azure** per archiviare il messaggio all'interno di una **tabella di Azure**.
- Configurare **Power bi** per la raccolta del messaggio archiviato e la creazione di un report.
- Visualizza i dati del messaggio Internet all'interno **Power bi**.

I servizi che si utilizzeranno includono:

- **Hub di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di connettersi, monitorare e gestire le risorse del tutto. Per altre informazioni, visita la [pagina del **servizio Hub Azure** ](https://azure.microsoft.com/services/iot-hub/).

- **Azure container Registry** è un servizio di Microsoft Azure che consente agli sviluppatori di archiviare le immagini del contenitore per diversi tipi di contenitori. Per altre informazioni, visitare la [pagina del **servizio container Registry di Azure** ](https://azure.microsoft.com/services/container-registry/).

- **Azure app per le funzioni** è un servizio Microsoft Azure, che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure. Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, node. js, Java e php. Per altre informazioni, visitare la [pagina **funzioni di Azure** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Archiviazione di Azure: tabelle** è un servizio Microsoft Azure, che consente agli sviluppatori di archiviare dati strutturati e non SQL nel cloud, rendendoli facilmente accessibili ovunque. Il servizio presenta una progettazione senza schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile. Per altre informazioni, visita la [pagina delle **tabelle di Azure**](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Questo corso ti insegnerà come configurare e usare il servizio hub Internet delle cose e quindi visualizzare una risposta fornita da un dispositivo. Sarà quindi necessario applicare questi concetti a una configurazione del servizio Hub delle cose personalizzate, che può essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 313: servizio hub Internet</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

Per i prerequisiti più aggiornati per lo sviluppo con realtà mista, tra cui con Microsoft HoloLens, vedere l'articolo [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Python. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Sono necessari i componenti hardware e software seguenti:

- Windows 10 Fall Creators Update (o versione successiva), **modalità sviluppatore abilitata**

    > [!WARNING]
    > Non è possibile eseguire una macchina virtuale con Hyper-V in Windows 10 Home Edition.

- Windows 10 SDK (versione più recente)
- HoloLens, **modalità sviluppatore abilitata**
- Visual Studio 2017.15.4 (usato solo per accedere al Cloud Explorer di Azure)
- Accesso a Internet per Azure e per il servizio hub Internet. Per altre informazioni, seguire questo [collegamento alla pagina del servizio Hub](https://azure.microsoft.com/services/iot-hub/) Internet.
- Un modello di machine learning. Se non si dispone di un modello pronto per l'utilizzo, [è possibile utilizzare il modello fornito con questo corso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- Software **Hyper-V** abilitato nel computer di sviluppo Windows 10.
- Una macchina virtuale che esegue Ubuntu (16,4 o 18,4), in esecuzione nel computer di sviluppo o in alternativa, è possibile usare un computer separato che esegue Linux (Ubuntu 16,4 o 18,4). Per ulteriori informazioni su come creare una macchina virtuale in Windows utilizzando Hyper-V, vedere il [capitolo "prima di iniziare"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Prima di iniziare

1. Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).
2. Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la **taratura** e l' **ottimizzazione dei sensori** , a volte può essere utile per eseguire queste attività per ogni utente.

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

3. Configurare la **macchina virtuale Ubuntu** con **Hyper-V**. Le risorse seguenti consentiranno di semplificare il processo.
    1.  Per prima cosa, seguire questo collegamento per [scaricare l'immagine ISO 16.04.4 LTS (xenial Xerus) di Ubuntu](https://au.releases.ubuntu.com/16.04/). Selezionare l' **immagine del desktop di 64 bit per PC (amd64)** .
    2.  Verificare che **Hyper-V** sia abilitato nel computer Windows 10. È possibile seguire questo collegamento per istruzioni sull' [installazione e l'abilitazione di Hyper-V in Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Avviare Hyper-V e creare una nuova macchina virtuale Ubuntu. È possibile seguire questo collegamento per una [Guida dettagliata su come creare una macchina virtuale con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Quando viene richiesto di **installare un sistema operativo da un file di immagine di avvio**, selezionare l'immagine ISO di **Ubuntu** scaricata in precedenza.

    > [!NOTE]
    > Non è consigliabile usare la **creazione rapida di Hyper-V** .  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capitolo 1-recuperare il modello di Visione personalizzata

Con questo corso potrai accedere a un [modello di visione personalizzata](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) predefinito che rileva tastiere e topi dalle immagini. Se si usa questa operazione, procedere con il [capitolo 2](#chapter-2---the-container-registry-service).

Tuttavia, se si vuole usare il proprio modello di Visione personalizzata, è possibile seguire questa procedura:

1. Nel **progetto visione personalizzata** passare alla scheda **prestazioni** .

    > [!WARNING]
    > Per esportare il modello, il modello deve usare un dominio *compatto* . È possibile modificare il dominio dei modelli nelle impostazioni per il progetto.

    ![scheda prestazioni](images/AzureLabs-Lab313-01.png)

2. Selezionare l' **iterazione** che si desidera esportare e fare clic su **Esporta**. Verrà visualizzato un pannello.

    ![pannello Esporta](images/AzureLabs-Lab313-02.png)

3. Nel pannello fare clic su **file Docker**.

    ![Selezionare Docker](images/AzureLabs-Lab313-03.png)

4. Scegliere **Linux** dal menu a discesa e quindi fare clic su **download**.

    ![Fare clic su download](images/AzureLabs-Lab313-04.png)

5. Decomprimere il contenuto. Che verrà usato più avanti in questo corso.

## <a name="chapter-2---the-container-registry-service"></a>Capitolo 2-Servizio Container Registry

Il **servizio container Registry** è il repository usato per ospitare i contenitori.

Il **servizio Hub** Internet delle cose che verrà compilato e usato in questo corso fa riferimento al **servizio container Registry** per ottenere i contenitori da distribuire nel dispositivo perimetrale.

1. Per prima cosa, seguire questo [collegamento al portale di Azure](https://portal.azure.com/)e accedere con le proprie credenziali.

2. Passare a **Crea una risorsa** e cercare **container Registry**.

    ![registro contenitori](images/AzureLabs-Lab313-05.png)

3. Fare clic su **Crea**.

    ![](images/AzureLabs-Lab313-06.png)

4. Impostare i parametri di installazione del servizio:

    1. Inserire un nome per il progetto, in questo esempio denominato **IoTCRegistry**.

    2. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

    3. Imposta il percorso del servizio.

    4. Impostare **utente amministratore** su **Abilita**.

    5. Impostare **SKU** su **Basic**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Fare clic su **Crea** e attendere la creazione dei servizi. 

6. Quando viene visualizzata la notifica che informa che la creazione del *container Registry*è riuscita, fare clic su **Vai alla risorsa** da reindirizzare alla pagina del servizio.

    ![](images/AzureLabs-Lab313-08.png)

7. Nella pagina servizio *container Registry* fare clic su **chiavi di accesso**.

8. Prendere nota (è possibile usare il blocco note) dei parametri seguenti:
    1. **Server di accesso**
    2. **Nome utente**
    3. **Password**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capitolo 3-servizio hub Internet delle cose

A questo punto si inizierà la creazione e la configurazione del **servizio Hub**Internet delle cose.

1. Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2.  Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare l' **Hub**Internet e premere **invio**.

 ![Cerca account di archiviazione](images/AzureLabs-Lab313-10.png)

3.  La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** . Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'istanza del servizio.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-11.png)

4.  Una volta fatto clic su **Crea**, verrà visualizzato un pannello:

    1. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Selezionare un **percorso** appropriato (usare la stessa posizione in tutti i servizi creati in questo corso).

    3. Inserire il **nome** desiderato per l'istanza del servizio.    

5.  Nella parte inferiore della pagina fare clic su **Next: size and scale**.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-12.png)

6.  In questa pagina selezionare il piano **tariffario e il livello di scalabilità** (se si tratta della prima istanza del servizio hub Internet, sarà disponibile un livello gratuito).  

7.  Fare clic su **Verifica + crea**.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-13.png)

8.  Verificare le impostazioni e fare clic su **Crea**.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-14.png)

9. Quando viene visualizzata la notifica che informa che la creazione del servizio *Hub* Internet è stata completata, fare clic su **Vai alla risorsa** da reindirizzare alla pagina del servizio.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-15.png)

10. Scorrere il pannello laterale a sinistra fino a quando non viene visualizzata la *gestione automatica dei dispositivi*, facendo clic su **IOT Edge**.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-16.png)

11. Nella finestra visualizzata a destra fare clic su **aggiungi IOT Edge dispositivo**. Verrà visualizzato un pannello a destra.

12. Nel pannello fornire al nuovo dispositivo un **ID dispositivo** , ovvero un nome di propria scelta. Quindi, fare clic su **Salva**. Le chiavi *primarie* e *secondarie* vengono generate automaticamente se è stato **generato automaticamente** il segno di generazione.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-17.png)

13. Si tornerà alla sezione *dispositivi IOT Edge* , in cui verrà elencato il nuovo dispositivo. Fare clic sul nuovo dispositivo (descritto in rosso nell'immagine seguente). 

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-18.png)

14. Nella pagina *Dettagli dispositivo* visualizzata, eseguire una copia della **stringa di connessione** (chiave primaria).

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-19.png)

15. Tornare al pannello a sinistra e fare clic su criteri di *accesso condiviso*per aprirlo. 

16. Nella pagina visualizzata fare clic su **iothubowner**. verrà visualizzato un pannello a destra della schermata. 

17. Prendere nota (sul blocco note) della **stringa di connessione** (chiave primaria), da usare in un secondo momento quando si imposta la *stringa di connessione* sul dispositivo.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capitolo 4-configurazione dell'ambiente di sviluppo

Per creare e distribuire i moduli per il *perimetro dell'hub*Internet delle cose, è necessario che i componenti seguenti siano installati nel computer di sviluppo che esegue Windows 10:

1.  [Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), verrà richiesto di creare un account per poterlo scaricare. 

    [scaricare ![Docker per Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker richiede *Windows 10 Pro*, *Enterprise 14393*o *Windows Server 2016 RTM*per l'esecuzione. Se si eseguono altre versioni di Windows 10, è possibile provare a installare Docker usando la [casella degli strumenti di Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3,6](https://www.python.org/downloads/).

    [![scaricare Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (noto anche come vs code)](https://code.visualstudio.com/download).

    [Download ![VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Dopo aver installato il software menzionato in precedenza, sarà necessario riavviare il computer.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capitolo 5-configurazione dell'ambiente Ubuntu

A questo punto è possibile passare alla configurazione del dispositivo **che esegue Ubuntu OS**. Attenersi alla procedura seguente per installare il software necessario per distribuire i contenitori nella lavagna:

> [!IMPORTANT]
> È sempre necessario precedere i comandi del terminale con **sudo** per l'esecuzione come utente amministratore. cioè
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Aprire il **terminale Ubuntu**e usare il comando seguente per installare **PIP**:

    > [! HINT] è possibile aprire facilmente il *terminale* usando i tasti di scelta rapida: **CTRL + ALT + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  In questo capitolo, è possibile che venga richiesto, dal *terminale*, per l'autorizzazione all'uso dell'archiviazione del dispositivo e per l'input di **y/n** (Sì o no), digitare **"y"** , quindi premere il tasto **invio** per accettare.

3.  Al termine del comando, usare il comando seguente per installare **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Dopo l'installazione di **PIP** e **curl** , usare il comando seguente per installare il **runtime di IOT Edge**, necessario per distribuire e controllare i moduli sulla lavagna:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. A questo punto verrà chiesto di aprire il *file di configurazione di runtime*per inserire la stringa di **connessione del dispositivo**annotata (nel blocco note) quando si crea il **servizio Hub** Internet (nel[passaggio 14 del capitolo 3](#chapter-3---the-iot-hub-service)). Eseguire la riga seguente nel terminale per aprire il file:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Verrà visualizzato il file **config. YAML** , pronto per la modifica:

    > [!WARNING]
    > Quando si apre questo file, è possibile che si verifichi una certa confusione. Il file verrà modificato dal testo nel *terminale* stesso. 

    1.  Usare i tasti di direzione sulla tastiera per scorrere verso il basso (sarà necessario scorrere verso il basso), per raggiungere la riga contenente ":

        " **\<aggiungere la stringa di connessione del dispositivo qui >** ".

    2. Sostituire la riga, **incluse le parentesi**, con la **stringa di connessione del dispositivo** annotata in precedenza.

7. Con la stringa di connessione sul posto, sulla tastiera premere i tasti **CTRL + X** per salvare il file. Verrà richiesto di confermare digitando **Y**. Premere quindi il tasto **invio** per confermare. Si tornerà al *terminale*normale. 

8. Una volta che tutti i comandi sono stati eseguiti correttamente, il **runtime di IOT Edge**sarà installato. Una volta inizializzato, il runtime si avvierà in modo autonomo ogni volta che il dispositivo viene acceso e si troverà in background, in attesa che i moduli vengano distribuiti dal **servizio Hub**Internet delle cose.

9.  Eseguire la seguente riga di comando per inizializzare il *runtime di IOT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Se si apportano modifiche al file con estensione YAML o al programma di installazione precedente, sarà necessario eseguire nuovamente la riga di riavvio precedente, all'interno del *terminale*.

10. Verificare lo stato di *Runtime IOT Edge* eseguendo la riga di comando seguente. Il runtime verrà visualizzato con lo stato **attivo (in esecuzione)** in testo verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Premere i tasti **CTRL + C** per uscire dalla pagina stato. È possibile verificare che il *runtime di IOT Edge* stia effettuando correttamente il pull dei contenitori digitando il comando seguente:

    ```bash
        sudo docker ps
    ```

12. Verrà visualizzato un elenco con due contenitori (2). Si tratta dei moduli predefiniti che vengono creati automaticamente dal servizio hub Internet delle cose (edgeAgent e edgeHub). Una volta creati e distribuiti i moduli, questi verranno visualizzati in questo elenco, sotto quelli predefiniti.

## <a name="chapter-6---install-the-extensions"></a>Capitolo 6: installare le estensioni

> [!IMPORTANT]
> I prossimi capitoli (6-9) devono essere eseguiti nel computer Windows 10.

1. Aprire **vs code**.

2. Fare clic sul pulsante **estensioni** (quadrato) nella barra di sinistra di vs code per aprire il **Pannello estensioni**.

3. Cercare e installare le estensioni seguenti (come illustrato nell'immagine seguente):

    1. Azure IoT Edge
    2. Toolkit di Azure.
    3. Docker   

    ![Creare il contenitore](images/AzureLabs-Lab313-24.png)

4. Una volta installate le estensioni, chiuderlo e riaprirlo VS Code.

5. Con VS Code Apri ancora una volta, passare a **visualizza** > **terminale integrato**.

6. Si installerà ora **tagliatore**. Nel terminale eseguire il comando bash seguente:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT] Se si riscontrano problemi con questo comando: 
    >1. Riavviare VS Code e/o il computer.
    >2. Potrebbe essere necessario passare il **terminale vs code** a quello usato per installare Python, ad esempio **PowerShell** (soprattutto se l'ambiente Python è già installato nel computer). Con il terminale aperto è possibile trovare il menu a discesa sul lato destro del terminale.
     ![creare il contenitore](images/AzureLabs-Lab313-24b.png) 
    >3. Verificare che il percorso di installazione di **Python** venga aggiunto come **variabile di ambiente** nel computer. Tagliatore deve far parte dello stesso percorso. [Per ulteriori informazioni sulle variabili di ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), seguire questo collegamento. 

7. Al termine dell'installazione di **tagliatore** , è necessario riavviare il computer, in modo che **tagliatore** venga riconosciuto come comando nell'ambiente del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capitolo 7: creare una soluzione contenitore

A questo punto, è necessario creare il contenitore, con il modulo, per eseguire il push nel *container Registry*. Dopo aver eseguito il push del contenitore, si userà il servizio *Edge Hub* Internet per distribuirlo nel dispositivo, che esegue il runtime di *IOT Edge*.

1. In VS Code fare clic su **visualizza** > **tavolozza comandi**.

2. Nella tavolozza, cercare ed eseguire **Azure IOT Edge: nuova soluzione Edge**.

3. Individuare un percorso in cui si desidera creare la soluzione. Premere il tasto **invio** per accettare il percorso.

4. Assegnare un nome alla soluzione. Premere il tasto **invio** per confermare il nome fornito.

5. A questo punto verrà richiesto di scegliere il Framework modello per la soluzione. Fare clic su **modulo Python**. Premere il tasto **invio** per confermare la scelta.

6. Assegnare un nome al modulo. Premere il tasto **invio** per confermare il nome del modulo. Assicurarsi di prendere nota del nome del modulo (con il blocco note), perché verrà usato in un secondo momento.

7. Si noterà che nella tavolozza verrà visualizzato un indirizzo predefinito del *repository di immagini Docker* . L'aspetto sarà simile al seguente:

    **localhost: 5000/-nome del modulo-** . 

8. Elimina **localhost: 5000**e al suo posto inserire l'indirizzo del **Server di accesso** *container Registry* , annotato durante la creazione del servizio di **container Registry** ([nel passaggio 8 del capitolo 2](#chapter-2---the-container-registry-service)). Premere il tasto **invio** per confermare l'indirizzo.

9. A questo punto, verrà creata la soluzione contenente il modello per il modulo Python e la relativa struttura verrà visualizzata nella **scheda Esplora**, di vs code, sul lato sinistro dello schermo. Se la **scheda Esplora** non è aperta, è possibile aprirla facendo clic sul pulsante in primo piano nella barra a sinistra.

    ![Creare il contenitore](images/AzureLabs-Lab313-25.png)

10. L'ultimo passaggio per questo capitolo consiste nel fare clic e aprire il **file con estensione ENV**, nella **scheda Esplora**e aggiungere il **nome utente** e la **password**del *container Registry* . Questo file viene ignorato da git, ma quando si compila il contenitore, le credenziali verranno impostate per accedere al **servizio container Registry**.

    ![Creare il contenitore](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capitolo 8-modifica della soluzione contenitore

A questo punto è necessario completare la soluzione contenitore aggiornando i file seguenti:

- script Python *<span></span>Main. py* .
- *requirements. txt*.
- *Deployment. template. JSON*.
- *Dockerfile. amd64*

Si creerà quindi la cartella *images* usata dallo script Python per verificare la presenza di immagini corrispondenti al modello di *visione personalizzata*. Infine, si aggiungerà il file *labels. txt* , per facilitare la lettura del modello e il file *Model. PB* , che rappresenta il modello.

1. Con VS Code aperto, passare alla cartella del modulo e cercare lo script denominato **<span></span>Main. py**. Fare doppio clic per aprirlo.

2. Eliminare il contenuto del file e inserire il codice seguente:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Aprire il file denominato **requirements. txt**e sostituirne il contenuto con il codice seguente:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Aprire il file denominato **Deployment. template. JSON**e sostituirne il contenuto seguendo le linee guida seguenti:

    1. Poiché la struttura JSON è personalizzata, sarà necessario modificarla manualmente, invece di copiare un esempio di. Per semplificare questa operazione, usare l'immagine seguente come guida.
    2. Le aree che hanno un aspetto diverso per l'utente, ma che **non devono essere modificate sono evidenziate in giallo**.
    3. **Le sezioni che è necessario eliminare sono evidenziate in rosso.**
    4. Prestare attenzione a eliminare le parentesi quadre corrette e rimuovere anche le virgole.

        ![Creare il contenitore](images/AzureLabs-Lab313-27.png)

    5. Il file JSON completato dovrebbe essere simile all'immagine seguente (Tuttavia, con le differenze univoche: *nome utente/password/nome modulo/riferimenti modulo*):

        ![Creare il contenitore](images/AzureLabs-Lab313-28.png)

5.  Aprire il file denominato **Dockerfile. amd64**e sostituirne il contenuto con il codice seguente:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Fare clic con il pulsante destro del mouse sulla cartella sotto i **moduli** (il nome fornito in precedenza, nell'esempio più avanti, è denominato *pythonmodule*) e fare clic su **nuova cartella**. Denominare le **Immagini**della cartella.

7.  All'interno della cartella aggiungere alcune immagini che contengono il mouse o la tastiera. Si tratta delle immagini che verranno analizzate dal modello Tensorflow.

    > [!WARNING]
    > Se si usa un modello personalizzato, è necessario modificarlo in modo da riflettere i dati dei modelli personalizzati.

8.  A questo punto è necessario recuperare i file **labels. txt** e **Model. PB** dalla cartella del modello, che è stata precedentemente scaricata (o creata dal proprio **servizio visione artificiale personalizzato**), nel [capitolo 1](#chapter-1---retrieve-the-custom-vision-model). Dopo aver creato i file, posizionarli all'interno della soluzione, insieme ad altri file. Il risultato finale dovrebbe essere simile all'immagine seguente:

    ![Creare il contenitore](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capitolo 9: creare un pacchetto della soluzione come contenitore

1.  A questo punto è possibile creare il pacchetto dei file come contenitore ed eseguirne il push nel **container Registry di Azure**. All'interno VS Code aprire il *terminale integrato* (**visualizzare** > **terminale integrato** o **CTRL**+ **\`** ) e usare la riga seguente per accedere a **Docker** (sostituire i valori del comando con le credenziali del **container Registry di Azure (ACR)** ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Fare clic con il pulsante destro del mouse sul file **Deployment. template. JSON**e scegliere **Compila IOT Edge soluzione**. Questo processo di compilazione richiede molto tempo (a seconda del dispositivo), quindi prepararsi ad attendere. Al termine del processo di compilazione, un file **Deployment. JSON** sarà stato creato all'interno di una nuova cartella denominata **config**.

    ![Crea distribuzione](images/AzureLabs-Lab313-30.png)

3. Aprire di nuovo il **riquadro comandi** e cercare **Azure: Sign in (accedi**). Seguire le istruzioni usando le credenziali dell'account Azure. VS Code fornirà un'opzione per la *copia e l'apertura*, che consente di copiare il codice del dispositivo che sarà presto necessario e di aprire il Web browser predefinito. Quando viene richiesto, incollare il codice del dispositivo per autenticare il computer.

    ![copia e Apri](images/AzureLabs-Lab313-31.png)

4. Una volta effettuato l'accesso, si noterà che, nella parte inferiore del pannello di *esplorazione* , è presente una nuova sezione denominata **dispositivi dell'hub Azure**. Fare clic su questa sezione per espanderla.

    ![dispositivo perimetrale](images/AzureLabs-Lab313-32.png)

5. Se il dispositivo non è disponibile, è necessario fare clic con il pulsante destro del mouse su *dispositivi dell'hub Azure*, quindi fare clic su **Imposta stringa di connessione dell'hub Internet**. Si noterà che il **riquadro comandi** (nella parte superiore di vs code) richiederà di immettere la *stringa di connessione*. Si tratta della *stringa di connessione* annotata alla fine del [capitolo 3](#chapter-3---the-iot-hub-service). Premere il tasto **invio** dopo aver copiato la stringa in.    

6. Il dispositivo deve essere caricato e visualizzato. Fare clic con il pulsante destro del mouse sul nome del dispositivo e quindi scegliere **Crea distribuzione per singolo dispositivo**.

    ![Crea distribuzione](images/AzureLabs-Lab313-33b.png)

7. Verrà visualizzato un prompt di *Esplora file* , in cui è possibile passare alla cartella **config** e quindi selezionare il file **Deployment. JSON** . Con il file selezionato, fare clic sul pulsante **Seleziona manifesto di distribuzione Edge** .

    ![Crea distribuzione](images/AzureLabs-Lab313-34.png)

8. A questo punto è stato fornito il **servizio Hub** Internet con il manifesto per la distribuzione del contenitore, come modulo, dal **container Registry di Azure**, in modo da distribuirlo nel dispositivo.

9. Per visualizzare i messaggi inviati dal dispositivo all'hub Internet, fare di nuovo clic con il pulsante destro del mouse sul nome del dispositivo nella sezione **dispositivi dell'hub Azure** Internet Explorer, nel pannello di **esplorazione** e fare clic su Avvia il **monitoraggio del messaggio D2C**. I messaggi inviati dal dispositivo verranno visualizzati nel terminale di Visual Studio. Essere paziente, perché questa operazione potrebbe richiedere del tempo. Vedere il capitolo successivo per il debug e verificare se la distribuzione è stata completata correttamente.

Questo modulo consente ora di eseguire un'iterazione tra le immagini nella cartella **images** e di analizzarle, con ogni iterazione. Questo è ovviamente solo una dimostrazione di come ottenere il modello di apprendimento automatico di base per il funzionamento in un ambiente IoT Edge dispositivo. 

Per espandere la funzionalità di questo esempio, è possibile procedere in diversi modi. Un modo potrebbe includere il codice nel contenitore, che acquisisce le foto da una webcam connessa al dispositivo e salva le immagini nella cartella immagini. 

Un altro modo potrebbe copiare le immagini dal dispositivo Internet delle cose nel contenitore. Un modo pratico per eseguire questa operazione consiste nell'eseguire il comando seguente nel terminale del dispositivo Internet delle cose, ad esempio se si desidera automatizzare il processo. È possibile testare questo comando eseguendolo manualmente dal percorso della cartella in cui sono archiviati i file:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capitolo 10-debug del runtime di IoT Edge

Di seguito è riportato un elenco di righe di comando e suggerimenti che consentono di monitorare ed eseguire il debug dell'attività di messaggistica del *runtime di IOT Edge*, dal **dispositivo Ubuntu**. 

- Verificare lo stato di *Runtime IOT Edge* eseguendo la riga di comando seguente:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Ricordarsi di premere **CTRL + C**per completare la visualizzazione dello stato.

- Elenca i contenitori attualmente distribuiti. Se il *servizio Hub* Internet delle cose ha distribuito correttamente i contenitori, verranno visualizzati eseguendo la riga di comando seguente:

    ```bash
        sudo iotedge list
    ```

    Oppure

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Questo è un buon metodo per verificare se il modulo è stato distribuito correttamente, perché verrà visualizzato nell'elenco; in caso contrario, si vedranno **solo** *edgeHub* e *edgeAgent*.

- Per visualizzare i log del codice di un contenitore, eseguire la riga di comando seguente:

    ```bash
        journalctl -u iotedge
    ```

**Comandi utili per gestire il runtime di IoT Edge:**

-  Per eliminare tutti i contenitori nell'host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Per arrestare il *runtime di IOT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capitolo 11-creazione del servizio tabelle 

Tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure creando una risorsa di archiviazione.

1. Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2. Una volta effettuato l'accesso, fare clic su **Crea una risorsa**, nell'angolo in alto a sinistra e cercare **account di archiviazione**e premere **invio** per avviare la ricerca.

3. Una volta visualizzato, fare clic su **account di archiviazione: BLOB, file, tabelle, code** nell'elenco.

    ![Cerca account di archiviazione](images/AzureLabs-Lab313-35.png)

4. La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** . Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'istanza del servizio.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-36.png)

5. Una volta fatto clic su **Crea**, verrà visualizzato un pannello:

    1. Inserire il **nome** desiderato per l'istanza del servizio (*deve essere in lettere minuscole*).

    2. Per **modello di distribuzione**, fare clic su **Resource Manager**.

    3. Per **tipo di account**, usando il menu a discesa, fare clic su **archiviazione (utilizzo generico V1)** .

    4. Fare clic su un **percorso**appropriato.
    
    5. Per il menu a discesa **replica** , fare clic su **archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .

    6. Per **prestazioni**, fare clic su **standard**.

    7. Nella sezione **trasferimento sicuro obbligatorio** fare clic su **disabilitato**.

    8. Dal menu a discesa **sottoscrizione** fare clic su una sottoscrizione appropriata.

    9. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lasciare le **reti virtuali** **disabilitate**, se questa è un'opzione.

    11. Fai clic su **Crea**.

        ![specificare i dettagli di archiviazione](images/AzureLabs-Lab313-37.png)

6. Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

7. Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale. Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![nuova notifica di archiviazione](images/AzureLabs-Lab313-38.png)

8. Fare clic sul pulsante **Vai alla risorsa** nella notifica. verrà quindi eseguita la nuova pagina Panoramica dell'istanza del servizio di archiviazione.

    ![Vai alla risorsa](images/AzureLabs-Lab313-39.png)

9. Nella pagina Panoramica fare clic su **tabelle**sul lato destro.
    
    ![Tabelle](images/AzureLabs-Lab313-40.png)

10. Il pannello a destra cambierà in modo da visualizzare le informazioni sul **servizio tabelle** , in cui è necessario aggiungere una nuova tabella. A tale scopo, fare clic sul pulsante **+ tabella** nell'angolo superiore sinistro.

    ![Apri tabelle](images/AzureLabs-Lab313-41.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome di **tabella**. Si tratta del nome che verrà usato per fare riferimento ai dati nell'applicazione nei capitoli successivi (creazione di app per le funzioni e Power BI). Inserire **IoTMessages** come nome (è possibile sceglierne un altro, ricordarlo se usato più avanti in questo documento) e fare clic su **OK**. 

12. Una volta creata la nuova tabella, sarà possibile visualizzarla nella pagina del **servizio tabelle** (nella parte inferiore).

    ![nuova tabella creata](images/AzureLabs-Lab313-42.png)  

13. A questo punto, fare clic su **chiavi di accesso** e copiare il nome e la **chiave** dell' **account di archiviazione** (usando il blocco note). questi valori verranno usati più avanti in questo corso, quando si crea il app per le funzioni di **Azure**.

    ![nuova tabella creata](images/AzureLabs-Lab313-43.png) 

14. Utilizzando di nuovo il pannello a sinistra, scorrere fino alla sezione *servizio* tabelle, fare clic su **tabelle** (o **esplorare le tabelle**, in portali più recenti) ed eseguire una copia dell'URL della **tabella** (usando il blocco note). Questo valore verrà usato più avanti in questo corso, quando si collega la tabella all'applicazione **Power bi** .

    ![nuova tabella creata](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capitolo 12-completamento della tabella di Azure

Ora che l'account di archiviazione del **servizio tabelle** è stato configurato, è possibile aggiungervi dati, che verranno usati per archiviare e recuperare le informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1. Aprire **Visual Studio** (**non** Visual Studio Code).

2. Dal menu fare clic su **visualizza** > **Cloud Explorer**.

    ![Aprire Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. Il **Cloud Explorer** verrà aperto come elemento ancorato (essere paziente, perché il caricamento potrebbe richiedere tempo).

    > [!WARNING] 
    > Se la sottoscrizione usata per creare gli *account di archiviazione* non è visibile, assicurarsi di disporre di: 
    > - Si è connessi allo stesso account usato per il portale di Azure.
    > - È stata selezionata la sottoscrizione dalla pagina di gestione degli account. potrebbe essere necessario applicare un filtro dalle impostazioni dell'account:  
    >
    >   ![trova sottoscrizione](images/AzureLabs-Lab313-46.png)

4. Verranno visualizzati i servizi cloud di Azure. Trovare gli **account di archiviazione** e fare clic sulla freccia a sinistra di per espandere gli account.

    ![aprire gli account di archiviazione](images/AzureLabs-Lab313-47.png)

5. Una volta espansa, l' **account di archiviazione** appena creato dovrebbe essere disponibile. Fare clic sulla freccia a sinistra della risorsa di archiviazione, quindi, una volta espansa, trovare le **tabelle** e fare clic sulla freccia accanto a questa, per visualizzare la **tabella** creata nell'ultimo capitolo. Fare doppio clic sulla **tabella**.

6. La tabella verrà aperta al centro della finestra di Visual Studio. Fare clic sull'icona della tabella con il **+** (Plus).

    ![Aggiungi nuova tabella](images/AzureLabs-Lab313-48.png)

7. Verrà visualizzata una finestra con la richiesta di *aggiungere un'entità*. Si creerà solo un'entità, anche se avranno tre proprietà. Si noterà che *PartitionKey* e *RowKey* sono già disponibili, perché vengono usati dalla tabella per trovare i dati. 

    ![chiave di partizione e di riga](images/AzureLabs-Lab313-49.png)

8. Aggiornare i valori seguenti:

    - Nome: **PartitionKey**, valore: **PK_IoTMessages** 

    - Nome: **RowKey**, valore: **RK_1_IoTMessages** 

9. Quindi, fare clic su **Aggiungi proprietà** (in basso a sinistra della finestra *Aggiungi entità* ) e aggiungere la proprietà seguente:

    - **MessageContent**, sotto forma di *stringa*, lasciare vuoto il valore.

10. La tabella deve corrispondere a quella dell'immagine seguente:

    ![Aggiungi valori corretti](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Il motivo per cui l'entità ha il numero 1 nella chiave di riga è perché potrebbe essere necessario aggiungere altri messaggi, qualora si desideri sperimentare ulteriormente questo corso.

11. Al termine, fare clic su **OK** . La tabella è ora pronta per essere usata.

## <a name="chapter-13---create-an-azure-function-app"></a>Capitolo 13: creare una app per le funzioni di Azure 

A questo punto è necessario creare un *app per le funzioni di Azure*, che verrà chiamato dal *servizio Hub* Internet delle cose per archiviare i messaggi di *IOT Edge* dispositivo nel servizio **tabelle** , creato nel capitolo precedente.

In primo luogo, è necessario creare un file che consentirà alla funzione di Azure di caricare le librerie necessarie.

1.  Aprire il **blocco note** (premere il *tasto Windows*e digitare *notepad*).

    ![Apri blocco note](images/AzureLabs-Lab313-51.png)

2.  Con blocco note aperto, inserire la struttura JSON riportata di seguito. Una volta completata questa operazione, salvarla sul desktop come **Project. JSON**. Questo file definisce le librerie che la funzione utilizzerà. Se è stato usato NuGet, avrà un aspetto familiare.
    
    > [!WARNING]
    > È importante che la denominazione sia corretta; Assicurarsi che **non disponga di un'estensione di file txt** . Per informazioni di riferimento, vedere di seguito:
    >
    > ![Salvataggio JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Accedere al portale di [Azure](https://portal.azure.com).

4.  Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare **app per le funzioni**e premere il tasto **invio** per eseguire la ricerca. Fare clic su *app per le funzioni* nei risultati per aprire un nuovo pannello.

    ![Cerca app per le funzioni](images/AzureLabs-Lab313-53.png)

5.  Il nuovo pannello fornirà una descrizione del servizio **app per le funzioni** . Nella parte inferiore sinistra di questo pannello fare clic sul pulsante **Crea** per creare un'associazione con il servizio.

    ![istanza dell'app per le funzioni](images/AzureLabs-Lab313-54.png)

6.  Una volta fatto clic su **Crea**, compilare quanto segue:

    1. Per **nome app**, inserire il nome desiderato per l'istanza del servizio.

    2. Selezionare una **sottoscrizione**.

    3. Selezionare il piano tariffario appropriato, se è la prima volta che si crea un **servizio app per le funzioni**, sarà disponibile un livello gratuito.

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Per **sistema operativo**, fare clic su Windows, che corrisponde alla piattaforma desiderata.

    6. Selezionare un **piano di hosting** . questa esercitazione usa un **piano a consumo**.

    7. Selezionare un **percorso** (scegliere la stessa posizione della risorsa di archiviazione compilata nel passaggio precedente)

    8. Per la sezione **archiviazione** **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.

    9. Non sarà necessario *Application Insights* in questa app, quindi è possibile lasciarla **disattivata**.

    10. Fai clic su **Crea**.

        ![Crea nuova istanza](images/AzureLabs-Lab313-55.png)

7.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

8.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica](images/AzureLabs-Lab313-56.png)

9.  Fare clic sulla notifica, una volta completata la distribuzione.

10. Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. 

    ![Vai alla risorsa](images/AzureLabs-Lab313-57.png)

11. Sul lato sinistro del nuovo pannello fare clic sull'icona **+** (più) accanto a *funzioni*per creare una nuova funzione.

    ![Aggiungi nuova funzione](images/AzureLabs-Lab313-58.png)

12. All'interno del pannello centrale verrà visualizzata la finestra di creazione della **funzione** . Scorrere ulteriormente verso il basso e fare clic su **funzione personalizzata**.

    ![funzione personalizzata](images/AzureLabs-Lab313-59.png)

13. Scorrere verso il basso la pagina successiva finché non viene trovato l'hub delle cose **(hub eventi)** , quindi fare clic su di esso.

    ![funzione personalizzata](images/AzureLabs-Lab313-60.png)

14. Nel **Pannello Hub eventi (hub eventi)** impostare la **lingua** su **C#** e quindi fare clic su **nuovo**.

    ![funzione personalizzata](images/AzureLabs-Lab313-61.png)

15. Nella finestra che verrà visualizzata verificare che sia selezionata l'opzione **Hub** Internet e che il nome del campo dell' *Hub* Internet corrisponda al nome del *servizio Hub* Internet che è stato creato in precedenza ([nel passaggio 8 del capitolo 3](#chapter-3---the-iot-hub-service)). Fare quindi clic sul pulsante **Seleziona** .

    ![funzione personalizzata](images/AzureLabs-Lab313-62.png)

16. Tornare al **Pannello Hub eventi (hub eventi)** , fare clic su **Crea**.

    ![funzione personalizzata](images/AzureLabs-Lab313-63.png)

17. Si verrà reindirizzati all'editor di funzioni.

    ![funzione personalizzata](images/AzureLabs-Lab313-64.png)

18. Eliminare tutto il codice e sostituirlo con quanto segue:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Modificare le variabili seguenti, in modo che corrispondano ai valori appropriati (valori di**tabella** e di **archiviazione** , [rispettivamente dal passaggio 11 e 13 del capitolo 11](#chapter-11---create-table-service)), che si troveranno nell'account di **archiviazione**:

    - **TableName**, con il nome della **tabella** che si trova nell' **account di archiviazione**.
    - **tableURL**, con l'URL della **tabella** che si trova nell' **account di archiviazione**.
    - **storageAccountName**, con il nome del valore corrispondente al nome del nome dell' **account di archiviazione** .
    - **storageAccountKey**, con la chiave ottenuta nel servizio di archiviazione creato in precedenza.

    ![funzione personalizzata](images/AzureLabs-Lab313-65.png)

20. Con il codice sul posto, fare clic su **Salva**.

21. Fare quindi clic sull'icona **\<** (freccia), sul lato destro della pagina.

    ![funzione personalizzata](images/AzureLabs-Lab313-66.png)

22. Un pannello scorrerà verso destra. In tale pannello fare clic su **carica**e verrà visualizzato un *browser file* .

23. Passare a e fare clic sul file **Project. JSON** , creato in precedenza nel **blocco note** , quindi fare clic sul pulsante **Apri** . Questo file definisce le librerie che la funzione utilizzerà.

    ![funzione personalizzata](images/AzureLabs-Lab313-67.png)

24. Quando il file è stato caricato, verrà visualizzato nel pannello a destra. Facendo clic su di esso verrà aperto nell'editor di **funzioni** . Deve essere **esattamente** uguale all'immagine successiva.

    ![funzione personalizzata](images/AzureLabs-Lab313-68.png)

25. A questo punto sarebbe opportuno testare la funzionalità della funzione per archiviare il messaggio nella *tabella*. Sul lato superiore destro della finestra fare clic su **test**.

    ![funzione personalizzata](images/AzureLabs-Lab313-69.png)

26. Inserire un messaggio sul **corpo della richiesta**, come illustrato nell'immagine precedente, e fare clic su **Run (Esegui**). 

27. La funzione verrà eseguita, visualizzando lo stato del risultato (si noterà lo **stato verde 202 accettato**, sopra la finestra di *output* , il che significa che è stata effettuata una chiamata riuscita):

    ![Risultato output](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capitolo 14-visualizzare i messaggi attivi

Se ora si apre Visual Studio (**non** Visual Studio Code), è possibile visualizzare il risultato del messaggio di test, in quanto verrà archiviato nell'area della stringa *MessageContent* .

![funzione personalizzata](images/AzureLabs-Lab313-71.png)

Con il servizio tabelle e app per le funzioni sul posto, i messaggi di Ubuntu Device verranno visualizzati nella tabella *IoTMessages* . Se non è già in esecuzione, riavviare il dispositivo e sarà possibile visualizzare i messaggi di risultato dal dispositivo e il modulo nella tabella tramite l'uso di Visual Studio *Cloud Explorer*.

![Visualizza dati](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capitolo 15-installazione di Power BI

Per visualizzare i dati dal dispositivo Internet delle cose, configurare **Power bi** (versione desktop), per raccogliere i dati dal servizio *tabelle* appena creato. La versione *HoloLens* di Power bi utilizzerà quindi i dati per visualizzare il risultato.

1.  Aprire il Microsoft Store in Windows 10 e cercare **Power bi desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Scaricare l'applicazione. Al termine del download, aprirlo.

3.  Accedere a *Power bi* con l' **account di Microsoft 365**. Per iscriversi, è possibile essere reindirizzati a un browser. Una volta effettuata l'iscrizione, tornare all'app Power BI ed eseguire di nuovo l'accesso.

4.  Fare clic su **Ottieni dati** , quindi fare clic su **altro.**

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Fare clic su **Azure**, **archiviazione tabelle di Azure**e quindi su **Connetti**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Verrà richiesto di inserire l'URL della **tabella** raccolto in precedenza ([nel passaggio 13 del capitolo 11](#chapter-11---create-table-service)), durante la creazione del servizio tabelle. Dopo aver inserito l'URL, eliminare la parte del percorso che fa riferimento alla tabella "subfolder" (che è stata IoTMessages, in questo corso). Il risultato finale dovrebbe essere come visualizzato nell'immagine seguente. Fare quindi clic su **OK**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Verrà richiesto di inserire la chiave di **archiviazione** annotata ([nel passaggio 11 del capitolo 11) in](#chapter-11---create-table-service)precedenza durante la creazione dell'archiviazione tabelle. Fare quindi clic su **Connetti**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Verrà visualizzato un **Pannello dello strumento di navigazione** , quindi selezionare la casella accanto alla tabella e fare clic su **carica**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabella è stata caricata in Power BI, ma richiede una query per visualizzare i valori in esso contenuti. A tale scopo, fare clic con il pulsante destro del mouse sul nome della tabella che si trova nel **Pannello campi** sul lato destro dello schermo. Quindi fare clic su **modifica query**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Un **Editor Power query** si aprirà come nuova finestra, visualizzando la tabella. Fare clic sul **record** di parole nella colonna *contenuto* della tabella per visualizzare il contenuto archiviato.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Fare clic su **nella tabella**nella parte superiore sinistra della finestra. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Fare clic su **chiudi & applica**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Al termine del caricamento della query, all'interno del **Pannello campi**, sul lato destro dello schermo, selezionare le caselle corrispondenti al **nome** e al **valore**dei parametri per visualizzare il contenuto della colonna **MessageContent** .

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Fare clic sull' **icona del disco Blu** nella parte superiore sinistra della finestra per salvare il lavoro in una cartella di propria scelta.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. È ora possibile fare clic sul pulsante pubblica per caricare la tabella nell'area di lavoro. Quando richiesto, fare clic su **area di lavoro personale** e fare clic su *Seleziona*. Attendere che visualizzi il risultato corretto dell'invio.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Il capitolo seguente è specifico di HoloLens. Power BI non è attualmente disponibile come applicazione immersiva, ma è possibile eseguire la versione desktop nel portale per la realtà mista di Windows (noto anche come Cliff House), tramite l'app desktop.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capitolo 16: visualizzare i dati Power BI in HoloLens

1. Nella HoloLens accedere al **Microsoft Store**, toccando la relativa icona nell'elenco delle applicazioni.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Cercare e scaricare l'applicazione **Power bi** .

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Avviare **Power bi** dall'elenco delle applicazioni. 

4. **Power bi** possibile richiedere l'accesso all'account di **Microsoft 365**.

5. Una volta all'interno dell'app, l'area di lavoro verrà visualizzata per impostazione predefinita, come illustrato nell'immagine seguente. Se ciò non accade, è sufficiente fare clic sull'icona dell'area di lavoro sul lato sinistro della finestra.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>L'applicazione dell'hub Internet è stata completata

Congratulazioni, è stato creato un servizio hub Internet delle cose con un dispositivo periferico della macchina virtuale simulato. Il dispositivo può comunicare i risultati di un modello di apprendimento automatico a un servizio tabelle di Azure, semplificato da un app per le funzioni di Azure, che viene letto in Power BI e visualizzato all'interno di una HoloLens Microsoft.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Espandere la struttura di messaggistica archiviata nella tabella e visualizzarla come grafico. È possibile che si desideri raccogliere più dati e archiviarli nella stessa tabella per essere visualizzati in un secondo momento.

### <a name="exercise-2"></a>Esercizio 2

Creare un ulteriore modulo "acquisizione fotocamera" da distribuire nella bacheca degli utenti, in modo che possa acquisire immagini attraverso la fotocamera da analizzare.
