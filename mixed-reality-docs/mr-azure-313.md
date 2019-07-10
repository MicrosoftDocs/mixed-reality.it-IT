---
title: MR e 313 - servizio Hub IoT di Azure
description: Completare questo corso di informazioni su come implementare il servizio Hub IoT di Azure in una macchina virtuale che esegue Ubuntu 16.4 e quindi visualizzare i dati del messaggio usando Microsoft HoloLens o un auricolare (VR) coinvolgenti.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realtà mista, Azure, academy, edge, iot edge, esercitazione, api, la notifica, funzioni, tabelle, hololens, coinvolgenti, vr, iot, macchina virtuale, ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694593"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR e Azure 313: Servizio Hub IoT

![risultato del corso](images/AzureLabs-Lab313-00.png)

In questo corso, si apprenderà come implementare un' **servizio Hub IoT di Azure** in una macchina virtuale in esecuzione il sistema operativo Ubuntu 16.4. Un' **App per le funzioni** verrà usato per ricevere messaggi da una VM Ubuntu e archiviare il risultato all'interno di un' **servizio tabelle di Azure**. Quindi sarà possibile visualizzare questo dati usando **Power BI** in Microsoft HoloLens o coinvolgenti visore VR (VR).

Il contenuto di questo corso *applicabile* nei dispositivi perimetrali IoT, ma ai fini di questo corso, lo stato attivo si sarà in un ambiente di macchina virtuale, in modo che l'accesso a un dispositivo fisico di Edge non è necessario.

Completando questo corso, apprenderà come:

- Distribuire un' **modulo di IoT Edge** a una macchina virtuale (sistema operativo di Ubuntu 16), che rappresenterà un dispositivo IoT.
- Aggiungere un **modello di Azure Custom Vision Tensorflow** per il modulo di Edge, con il codice che analizza le immagini archiviate nel contenitore.
- Configurare il modulo per inviare il messaggio di risultato di analisi al **il servizio Hub IoT**.
- Usa un' **App per le funzioni** per memorizzare il messaggio all'interno di un' **tabelle di Azure**.
- Configurare **Power BI** per raccogliere il messaggio archiviato e creare un report.
- Visualizzare i dati di messaggio IoT entro **Power BI**.

I servizi che si utilizzeranno includono:

- **IoT Hub di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di connettere, monitorare e gestire, gli asset IoT. Per altre informazioni, visitare il [ **servizio Hub IoT di Azure** pagina](https://azure.microsoft.com/en-au/services/iot-hub/).

- **Registro contenitori di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di archiviare immagini dei contenitori, per vari tipi di contenitori. Per altre informazioni, visitare il [ **servizio Registro di sistema contenitore di Azure** pagina](https://azure.microsoft.com/en-au/services/container-registry/).

- **App per le funzioni Azure** è un servizio Microsoft Azure, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure. Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP. Per altre informazioni, visitare il [ **funzioni di Azure** pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Archiviazione di Azure: Tabelle** è un servizio Microsoft Azure, che consente agli sviluppatori di archiviare strutturati, non SQL, i dati nel cloud, per renderla facilmente accessibile ovunque. Il servizio vanta una struttura senza schema, che consente l'evoluzione delle tabelle in base alle esigenze ed è pertanto molto flessibile. Per altre informazioni, visitare il [ **le tabelle di Azure** pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Questo corso ti spiegherà come impostare e usare il servizio Hub IoT e quindi visualizzare una risposta fornita da un dispositivo. Sarà quindi compito è possibile applicare questi concetti per un'installazione personalizzata del servizio Hub IoT, che potrebbe voler costruire.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 313: Servizio Hub IoT</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

Per i prerequisiti per lo sviluppo con realtà mista, tra cui con il Microsoft HoloLens, più aggiornati, visitare il [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) articolo.

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Python. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quelli elencati di seguito.

È necessario hardware e software seguenti:

- Windows 10 Fall Creators Update (o versione successiva), **abilitata la modalità sviluppatore**

    > [!WARNING]
    > Non è possibile eseguire una macchina virtuale utilizzando Hyper-V in Windows 10 Home Edition.

- Windows 10 SDK (versione più recente)
- A HoloLens, **abilitata la modalità sviluppatore**
- Visual Studio 2017.15.4 (usato solo per accedere a Esplora il Cloud Azure)
- Accesso a Internet per Azure e per il servizio Hub IoT. Per altre informazioni, seguire questa [collegamento alla pagina del servizio Hub IoT](https://azure.microsoft.com/en-au/services/iot-hub/)
- Un modello di machine learning. Se non è proprio pronti all'uso del modello, [è possibile usare il modello fornito con questo corso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Hyper-V** software abilitato nel computer di sviluppo di Windows 10.
- Una macchina virtuale che esegue Ubuntu 16.4 o 18.4, in esecuzione nel computer di sviluppo o in alternativa è possibile usare un computer separato che esegue Linux (Ubuntu 16.4 o 18.4). È possibile trovare altre informazioni su come creare una macchina virtuale su Windows con Hyper-V nel [capitolo "Prima di iniziare"](#before-you-start). ( https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Prima di iniziare

1. Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).
2. È una buona idea eseguire **calibrazione** e **sensore ottimizzazione** quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

3. Configurare le **macchina virtuale Ubuntu** utilizzando **Hyper-V**. Le risorse seguenti consentono del processo.
    1.  In primo luogo, fare clic sul collegamento a [scaricare l'immagine ISO LTS (Xenial Xerus) Ubuntu 16.04.4](http://au.releases.ubuntu.com/16.04/). Selezionare il **immagine del desktop PC (AMD64) a 64 bit**.
    2.  Assicurarsi che **Hyper-V** è abilitato nel computer Windows 10. È possibile seguire questo collegamento per indicazioni [installazione e abilitazione di Hyper-V in Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Avviare Hyper-V e creare una nuova VM di Ubuntu. È possibile seguire questo collegamento per una [Guida dettagliata su come creare una macchina virtuale con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Quando richiesto **"Installa un sistema operativo da un file di immagine di avvio"** , selezionare la **Ubuntu ISO** essere stati scaricati in precedenza.

    > [!NOTE]
    > Usando **creazione rapida di Hyper-V** non è consigliata.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capitolo 1: recuperare il modello di visione artificiale personalizzato

Con questo corso si avrà accesso a un [modello di visione artificiale personalizzato preesistente](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) che rileva tastiere e mouse dalle immagini. Se si usa questo, passare a [capitolo 2](#chapter-2---the-container-registry-service).

Tuttavia, è possibile seguire questi passaggi se si vuole usare il proprio modello di visione artificiale personalizzato:

1. Nel **progetto di visione artificiale personalizzato** andare alla **prestazioni** scheda.

    > [!WARNING]
    > Il modello è necessario usare una *compact* dominio, per esportare il modello. È possibile modificare il dominio di modelli nelle impostazioni per il progetto.

    ![scheda prestazioni](images/AzureLabs-Lab313-01.png)

2. Selezionare il **iterazione** si vuole esportare e fare clic su **esportare**. Verrà visualizzato un pannello.

    ![Pannello esportazione](images/AzureLabs-Lab313-02.png)

3. Nel pannello fare clic su **File Docker**.

    ![Selezionare docker](images/AzureLabs-Lab313-03.png)

4. Fare clic su **Linux** nel menu a tendina e quindi fare clic su **scaricare**.

    ![Fare clic su download](images/AzureLabs-Lab313-04.png)

5. Decomprimere il contenuto. Si userà, più avanti in questo corso.

## <a name="chapter-2---the-container-registry-service"></a>Capitolo 2: il servizio contenitore di registro di sistema

Il **servizio contenitore di registro di sistema** è il repository usato per ospitare i contenitori.

Il **il servizio Hub IoT** che di compilazione e verrà utilizzato in questo corso, si intende **contenitore del Registro di sistema servizio** per ottenere i contenitori da distribuire nel dispositivo Edge.

1. Seguire prima di tutto ciò [collegamento al portale di Azure](https://portal.azure.com/)e accedere con le proprie credenziali.

2. Passare a **crea una risorsa** e cercare **registro contenitori di**.

    ![Registro contenitori](images/AzureLabs-Lab313-05.png)

3. Fare clic su **creare**.

    ![](images/AzureLabs-Lab313-06.png)

4. Impostare il servizio di parametri di installazione:

    1. Inserire un nome per il progetto, In questo esempio la chiamata **IoTCRegistry**.

    2. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

    3. Impostare il percorso del servizio.

    4. Impostare **l'utente amministratore** al **abilitare**.

    5. Impostare **SKU** al **base**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Fare clic su **Create** e attendere che i servizi da creare. 

6. Una volta che viene visualizzata la notifica che informa della corretta creazione del *registro contenitori*, fare clic su **Vai alla risorsa** essere reindirizzati alla pagina del servizio.

    ![](images/AzureLabs-Lab313-08.png)

7. Nel *registro contenitori* pagina del servizio, fare clic su **chiavi di accesso**.

8. Prendere nota (è possibile usare il blocco note) dei parametri seguenti:
    1. **Login Server**
    2. **Nome utente**
    3. **Password**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capitolo 3 - il servizio Hub IoT

A questo punto si verrà avviata la creazione e l'installazione delle **il servizio Hub IoT**.

1. Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2.  Una volta effettuato l'accesso, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **dell'IoT Hub**, fare clic su **invio**.

 ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab313-10.png)

3.  La nuova pagina fornirà una descrizione del **account di archiviazione** servizio. AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'istanza di questo servizio.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-11.png)

4.  Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:

    1. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Selezionare un'opzione appropriata **posizione** (usare la stessa località in tutti i servizi creati in questo corso).

    3. Inserire la posizione desiderata **nome** per questa istanza del servizio.    

5.  Nella parte inferiore della pagina fare clic su **successiva: Ridimensionamento e scalabilità**.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-12.png)

6.  In questa pagina, selezionare i **piano tariffario e scalabilità livello** (se questa è la prima istanza di servizio dell'Hub IoT, un livello gratuito deve essere disponibile all'utente).  

7.  Fare clic su **Rivedi e crea**.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-13.png)

8.  Rivedere le impostazioni e fare clic su **Create**.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-14.png)

9. Una volta che viene visualizzata la notifica che informa della corretta creazione del *IoT Hub* servizio, fare clic su **Vai alla risorsa** essere reindirizzati alla pagina del servizio.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-15.png)

10. Pannello laterale a sinistra scorrere per visualizzare *gestione dei dispositivi automatici*, di fare clic su **IoT Edge**.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-16.png)

11. Nella finestra che viene visualizzato a destra, fare clic su **Aggiungi dispositivo IoT Edge**. Verrà visualizzato un pannello a destra.

12. Nel pannello del nuovo dispositivo forniscono un **ID dispositivo** (un nome di propria scelta). Fare quindi clic **salvare**. Il *primari* e *chiavi secondarie* auto genererà, se hai **genera automaticamente** selezionata.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-17.png)

13. Passerà nuovamente al *dispositivi perimetrali IoT* sezione, in cui verrà elencato il nuovo dispositivo. Fare clic sul nuovo dispositivo (evidenziate in rosso nell'immagine seguente). 

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-18.png)

14. Nel *dettagli dispositivo* pagina visualizzata, eseguire una copia della **stringa di connessione** (chiave primaria).

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-19.png)

15. Tornare al pannello a sinistra e fare clic su *criteri di accesso condiviso*per aprirlo. 

16. Nella pagina visualizzata, fare clic su **iothubowner**, e verrà visualizzato un pannello a destra della schermata. 

17. Prendere nota (on il blocco note) del **stringa di connessione** (chiave primaria), per utilizzarli successivamente quando l'impostazione di *stringa di connessione* al dispositivo.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capitolo 4 - impostazione dell'ambiente di sviluppo

Per creare e distribuire i moduli per *IoT Hub Edge*, saranno necessari i seguenti componenti installati nel computer di sviluppo che eseguono Windows 10:

1.  [Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), verrà chiesto di creare un account per poter scaricare. 

    [![scaricare docker per windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Richiede docker *Windows 10 PRO*, *Enterprise 14393*, o *Windows Server 2016 RTM*in modo da eseguire. Se si eseguono altre versioni di Windows 10, è possibile provare a installare Docker usando il [casella degli strumenti Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![scaricare python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (anche noto come VS Code)](https://code.visualstudio.com/download).

    [![scaricare Visual Studio Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Dopo aver installato il software indicato in precedenza, è necessario riavviare il computer.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capitolo 5: configurazione dell'ambiente di Ubuntu

A questo punto è possibile passare alla configurazione del dispositivo **che esegue OS Ubuntu**. Seguire la procedura seguente per installare il software necessario, per distribuire i contenitori nella bacheca:

> [!IMPORTANT]
> È sempre necessario far precedere i comandi di terminali con **sudo** per l'esecuzione come utente amministratore. ad esempio:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Aprire il **Ubuntu Terminal**e usare il comando seguente per installare **pip**:

    > [! HINT] è possibile aprire *Terminal* molto facilmente tramite il tasto di scelta rapida: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  In questo capitolo, è possibile che venga richiesto, da *Terminal*, l'autorizzazione per l'uso dell'archiviazione del dispositivo e sarà necessario immettere **s/n** (Sì o no), digitare **'y'** e quindi premere i **Invio** chiave, per accettare.

3.  Al termine di tale comando, usare il comando seguente per installare **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Una volta **pip** e **curl** vengono installati, usare il comando seguente per installare il **runtime di IoT Edge**, questa operazione è necessaria per distribuire e controllare i moduli nella bacheca:

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

5. A questo punto verrà richiesto di aprire il *file di configurazione di runtime*, inserire il **Device Connection String**, che si è preso nota (nel blocco note), quando si crea il **servizio Hub IoT**  ([al passaggio 14, capitolo 3](#chapter-3---the-iot-hub-service)). Eseguire la riga seguente nel terminale per aprire il file:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Il **config. yaml** file verranno visualizzati, è possibile modificare:

    > [!WARNING]
    > Quando si apre questo file, potrebbe essere una certa confusione. Si modifica questo file, all'interno del testo di *Terminal* stesso. 

    1.  Utilizzare i tasti di direzione sulla tastiera per scorrere verso il basso (è necessario scorrere verso il basso una piccola modo), per raggiungere la riga contenente ":

        " **\<AGGIUNGERE QUI STRINGA DI CONNESSIONE DEL DISPOSITIVO >** ".

    2. Riga, sostituire **incluse le parentesi**, con la **Device Connection String** annotato in precedenza.

7. Con la stringa di connessione posto, sulla tastiera, premere il **Ctrl-X** le chiavi per salvare il file. Verrà chiesto di confermare digitando **Y**. Premere quindi il **invio** chiave, per confermare. Si passerà nuovamente alla tariffa *Terminal*. 

8. Una volta che questi comandi hanno tutti eseguiti correttamente, verrà installato il **Runtime di IoT Edge**. Una volta inizializzato, il runtime verranno avviati con il proprio ogni volta che il dispositivo è acceso e il componente verrà posizionato in background, in attesa per i moduli per la distribuzione dal **il servizio Hub IoT**.

9.  Eseguire la seguente riga di comando per inizializzare il *Runtime di IoT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Se si apportano modifiche per il file con estensione yaml o la configurazione descritta sopra, dovrai eseguire di nuovo, la riga precedente di riavvio entro *Terminal*.

10. Verificare i *Runtime di IoT Edge* lo stato eseguendo la seguente riga di comando. Il runtime deve essere visualizzato con stato **attive in esecuzione** nel testo in verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Premere il **Ctrl + C** chiavi, per uscire dalla pagina relativa allo stato. È possibile verificare che il *Runtime di IoT Edge* effettua il pull dei contenitori correttamente, digitando il comando seguente:

    ```bash
        sudo docker ps
    ```

12. Dovrebbe essere visualizzato un elenco con i contenitori di due (2). Questi sono i moduli predefiniti vengono creati automaticamente dal servizio Hub IoT (edgeAgent ed edgeHub). Quando si creano e distribuiscono i propri moduli, verranno visualizzati nell'elenco, di sotto di quelli predefiniti.

## <a name="chapter-6---install-the-extensions"></a>Capitolo 6: installare le estensioni

> [!IMPORTANT]
> I prossimi capitoli descrivono (da 6 a 9) devono essere eseguite nel computer Windows 10.

1. Aprire **Visual Studio Code**.

2. Fare clic sui **Extensions** pulsante (quadrata) sul sinistro codice a barre di Visual Studio, aprire il **pannello estensioni**.

3. Cercare e installare, le estensioni seguenti (come illustrato nell'immagine seguente):

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![Creare il contenitore](images/AzureLabs-Lab313-24.png)

4. Una volta le estensioni vengono installate, chiudere e riaprire Visual Studio Code.

5. Con Visual Studio Code aprire ancora una volta, passare a **View** > **terminale integrato**.

6. A questo punto si installerà **Cookiecutter**. Nel terminale eseguire il comando bash seguente:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT] Se si riscontrano problemi con questo comando: 
    >1. Riavviare Visual Studio Code, e / o nel computer.
    >2. Potrebbe essere necessario passare il **terminale di Visual Studio Code** a quella a cui è stato utilizzato per installare Python, vale a dire **Powershell** (particolarmente nel caso in cui l'ambiente di Python è già stato installato nel computer). Aprire il terminale, sono disponibili nell'elenco a discesa dal menu sul lato destro della finestra del terminale.
     ![Creare il contenitore](images/AzureLabs-Lab313-24b.png) 
    >3. Assicurarsi che il **Python** percorso di installazione viene aggiunto come **variabile di ambiente** nel computer. Cookiecutter deve far parte di percorso stesso. Seguire questa [collegamento per altre informazioni sulle variabili di ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 

7. Una volta **Cookiecutter** è stato installato, è necessario riavviare il computer, in modo che **Cookiecutter** viene riconosciuto come un comando, nell'ambiente del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capitolo 7 - creare una soluzione contenitori

A questo punto, è necessario creare il contenitore, il modulo, eseguire il push nel *registro contenitori di*. Una volta che si è eseguito il push del contenitore, si userà il *Hub di IoT Edge* servizio distribuirla sul dispositivo, che è in esecuzione il *runtime di IoT Edge*.

1. Da Visual Studio Code, fare clic su **View** > **comandi**.

2. Nel riquadro di ricerca ed eseguire **Azure IoT Edge: Nuova soluzione Iot Edge**.

3. Sfoglia in una posizione in cui si desidera creare la soluzione. Premere il **invio** chiave, per accettare il percorso.

4. Assegnare un nome per la soluzione. Premere il **invio** chiave, per confermare il nome specificato.

5. A questo punto verrà chiesto di scegliere il framework di modello per la soluzione. Fare clic su **modulo Python**. Premere il **invio** chiave, per confermare la scelta.

6. Assegnare un nome per il modulo. Premere il **invio** chiave, per verificare il nome del modulo. Assicurarsi di annotare (con il blocco note) il nome del modulo, perché è usato in un secondo momento.

7. Si noterà una preesistente *Repository di immagini Docker* indirizzo verrà visualizzato nella tavolozza. Sarà simile al seguente:

    **localhost:5000 /, il nome del modulo -** . 

8. Eliminare **localhost:5000**e nel relativo inserimento sul posto di *registro contenitori* **Login Server** indirizzo, che si è preso nota quando si crea il **contenitore Servizio Registro di sistema** ([nel passaggio 8, capitolo 2](#chapter-2---the-container-registry-service)). Premere il **invio** chiave, per confermare l'indirizzo.

9. A questo punto, verrà creata la soluzione che contiene il modello per il modulo Python e la relativa struttura verrà visualizzata nei **esplorare scheda**, di Visual Studio Code, sul lato sinistro della schermata. Se il **esplorare scheda** è non è aperto, è possibile aprirlo facendo clic sul pulsante posizionata più in alto, nella barra a sinistra.

    ![Creare il contenitore](images/AzureLabs-Lab313-25.png)

10. L'ultimo passaggio per questo capitolo, deve fare clic e aprire il **file con estensione env**, dall'interno la **scheda Esplora**e aggiungere il *registro contenitori* **username** e **password**. Questo file viene ignorato da git, ma sulla compilazione imposterà le credenziali per accedere al contenitore e il **servizio contenitore di registro di sistema**.

    ![Creare il contenitore](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capitolo 8 - modifica la soluzione contenitori

A questo punto si completerà la soluzione contenitore, aggiornando i file seguenti:

- *principali<span></span>py* script python.
- *requirements.txt*.
- *deployment.template.json*.
- *Dockerfile.amd64*

Verrà quindi creato il *immagini* cartella usato dallo script di python per verificare la presenza di immagini in base alla quale confrontare i *modello di visione artificiale personalizzato*. Infine, si aggiungerà il *labels.txt* file, per facilitare la lettura del modello e il *model.pb* file, ovvero il modello.

1. Con Visual Studio Code aprire, passare alla cartella del modulo e cercare lo script chiamato **principale<span></span>py**. Fare doppio clic per aprirlo.

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

3.  Aprire il file denominato **Requirements. txt**e sostituire il contenuto con quanto segue:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Aprire il file denominato **deployment.template.json**e sostituire il contenuto seguente le seguenti linee guida:

    1. Poiché si avrà il proprio, univoca, struttura JSON, è necessario modificarlo manualmente (invece di copiare un esempio). Per facilitare questa operazione, usare l'immagine come guida seguente.
    2. Le aree che avrà un aspetto diverse rispetto a quelle in uso, ma che si **non deve cambiare viene evidenziato in giallo**.
    3. **Le sezioni che è necessario eliminare, sono una linea rossa evidenziata.**
    4. Prestare attenzione a eliminare la parentesi corrette e anche rimuovere le virgole.

        ![Creare il contenitore](images/AzureLabs-Lab313-27.png)

    5. Il codice JSON completato dovrebbe essere simile all'immagine seguente (tuttavia, con le differenze univoche: *riferimenti al nome utente/password/modulo nome/modulo*):

        ![Creare il contenitore](images/AzureLabs-Lab313-28.png)

5.  Aprire il file denominato **Dockerfile.amd64**e sostituire il contenuto con quanto segue:

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

6.  Pulsante destro del mouse sulla cartella sotto **moduli** (avrà il nome specificato in precedenza; nell'esempio ulteriormente verso il basso, viene chiamato *pythonmodule*) e fare clic su **nuova cartella**. Denominare la cartella **immagini**.

7.  All'interno della cartella, aggiungere alcune immagini contenenti mouse o tastiera. Che saranno le immagini che verranno analizzate dal modello Tensorflow.

    > [!WARNING]
    > Se si usa un modello personalizzato, è necessario modificare questa impostazione in modo da riflettere i propri dati di modelli.

8.  A questo punto è necessario recuperare il **labels.txt** e **model.pb** file dalla cartella di modello precedente scaricato (o creato dal proprio **servizio visione artificiale personalizzato** ), in [capitolo 1](#chapter-1---retrieve-the-custom-vision-model). Dopo aver creato i file, inserirli all'interno della soluzione, insieme ad altri file. Il risultato finale dovrebbe essere simile all'immagine seguente:

    ![Creare il contenitore](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capitolo 9 - pacchetto della soluzione come un contenitore

1.  A questo punto si è pronti per "pacchetto" i file come un contenitore ed eseguirne il push per le **registro contenitori di Azure**. All'interno di Visual Studio Code, aprire il *terminale integrato* (**View** > **terminale integrato** oppure **Ctrl** + **\`** ) e utilizzare la seguente riga per l'accesso al **Docker** (sostituire i valori del comando con le credenziali del **registro contenitori di Azure (ACR)** ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Fare doppio clic sul file **deployment.template.json**, fare clic su **Compila soluzione Edge IoT**. Questo processo di compilazione richiede molto tempo (a seconda del dispositivo), quindi sarà necessario attendere. Al termine del processo di compilazione, un **Deployment** file viene creato all'interno di una nuova cartella denominata **config**.

    ![creare una distribuzione](images/AzureLabs-Lab313-30.png)

3. Aprire il **riquadro comandi** anche in questo caso e cercare **Azure: Sign In**. Seguire le istruzioni usando le credenziali dell'Account di Azure; Visual Studio Code fornirà all'utente un'opzione per *copiare e aprire*, che verrà copiato il codice del dispositivo verrà presto necessarie e quindi aprire il web browser predefinito. Quando viene chiesto, incollare il codice del dispositivo, per eseguire l'autenticazione nel computer.

    ![copia e Apri](images/AzureLabs-Lab313-31.png)

4. Una volta firmati in si noterà, sul lato inferiore del *Explore* del pannello, una nuova sezione denominata **dispositivi dell'Hub IoT di Azure**. Fare clic su questa sezione per espanderla.

    ![dispositivo Edge](images/AzureLabs-Lab313-32.png)

5. Se il dispositivo non è in questo caso, sarà necessario fare doppio clic su *dispositivi dell'Hub IoT di Azure*, quindi fare clic su **Set IoT Hub Connection String**. Si noterà quindi che il **riquadro comandi** (nella parte superiore di Visual Studio Code), verrà richiesto di immettere il *stringa di connessione*. Questo è il *stringa di connessione* si è preso nota alla fine del [capitolo 3](#chapter-3---the-iot-hub-service). Premere il **invio** della chiave, dopo aver copiato la stringa.    

6. Il dispositivo deve caricare e vengono visualizzati. Fare doppio clic sul nome del dispositivo e quindi scegliere **creare la distribuzione per singolo dispositivo**.

    ![creare una distribuzione](images/AzureLabs-Lab313-33b.png)

7. Si otterrà un *Esplora File* prompt dei comandi, in cui è possibile passare alle **config** cartella e quindi selezionare il **Deployment** file. Con tale file selezionato, scegliere il **selezionare manifesto della distribuzione Edge** pulsante.

    ![creare una distribuzione](images/AzureLabs-Lab313-34.png)

8. A questo punto è stato specificato il **il servizio Hub IoT** con il manifesto per poter distribuire il contenitore, come un modulo, dalle **registro contenitori di Azure**, in modo efficace distribuirla nel dispositivo.

9. Per visualizzare i messaggi inviati dal dispositivo all'IoT Hub, fare clic nuovamente sul nome del dispositivo nel **dispositivi dell'Hub IoT di Azure** nella sezione la **Explorer** pannello e fare clic su **inizia il monitoraggio Messaggi D2C**. I messaggi inviati dal dispositivo verrà visualizzato nel terminale di Visual Studio. Essere paziente, in quanto l'operazione potrebbe richiedere qualche minuto. Vedere il capitolo successivo per il debug e verifica se la distribuzione è riuscita.

Questo modulo verrà ora eseguire l'iterazione tra le immagini nel **immagini** cartelle e analizzarli, con ogni iterazione. Questo è ovviamente solo una dimostrazione di come ottenere il modello di base di machine learning per lavorare in un ambiente del dispositivo IoT Edge. 

Per espandere la funzionalità di questo esempio, è possibile procedere in diversi modi. Uno dei modi potrebbe essere inclusi codice nel contenitore, che consente di acquisire foto da webcam che è connesso al dispositivo e Salva le immagini nella cartella delle immagini. 

Un altro modo possibile copiare le immagini dal dispositivo IoT nel contenitore. Un modo pratico per farlo consiste nell'eseguire il comando seguente nel dispositivo IoT terminale (forse una piccola app è stato possibile eseguire il processo, se si vuole automatizzare il processo). È possibile testare questo comando, eseguire manualmente dal percorso di cartella in cui sono archiviati i file:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capitolo 10 - debug Runtime di IoT Edge

Di seguito sono un elenco di righe di comando e suggerimenti, che consentono di monitorare ed eseguire il debug dell'attività di messaggistica la *Runtime di IoT Edge*, dalle **dispositivo Ubuntu**. 

- Verificare i *Runtime di IoT Edge* lo stato eseguendo la seguente riga di comando:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Tenere presente premere **Ctrl + C**per portare a termine visualizzando lo stato.

- Elencare i contenitori che sono attualmente distribuiti. Se il *il servizio Hub IoT* sia distribuito correttamente, i contenitori saranno visualizzati eseguendo la seguente riga di comando:

    ```bash
        sudo iotedge list
    ```

    Oppure

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Il codice precedente è un buon metodo per verificare se il modulo è stato distribuito correttamente, come verrà visualizzato nell'elenco. in caso contrario, verranno **soltanto** vedere la *edgeHub* e *edgeAgent*.

- Per visualizzare i log di codice di un contenitore, eseguire la seguente riga di comando:

    ```bash
        journalctl -u iotedge
    ```

**Comandi utili per gestire il Runtime di IoT Edge:**

-  Per eliminare tutti i contenitori nell'host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Per arrestare il *Runtime di IoT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capitolo 11 - Creazione del servizio tabelle 

Passare al portale di Azure, in cui verrà creato un servizio di tabelle di Azure, tramite la creazione di una risorsa di archiviazione.

1. Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2. Una volta effettuato l'accesso, fare clic su **crea una risorsa**in alto a sinistra angolo e cercare **account di archiviazione**, premere il **invio** chiave, per avviare la ricerca.

3. Dopo che è stato incluso, fare clic su **account di archiviazione: blob, file, tabella, coda** dall'elenco.

    ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab313-35.png)

4. La nuova pagina fornirà una descrizione del **account di archiviazione** servizio. AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'istanza di questo servizio.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-36.png)

5. Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:

    1. Inserire la posizione desiderata **Name** per questa istanza del servizio (*deve contenere solo lettere minuscole*).

    2. Per la **modello di distribuzione**, fare clic su **Resource manager**.

    3. Per la **tipologia Account**, usando il menu a discesa, fare clic su **archiviazione (utilizzo generico v1)** .

    4. Fare clic su un oggetto appropriato **posizione**.
    
    5. Per il **replica** dal menu a discesa, fare clic su **Read-access-archiviazione geograficamente ridondante (RA-GRS)** .

    6. Per la **Performance**, fare clic su **Standard**.

    7. All'interno di **trasferimento sicuro obbligatorio** fare clic su **disabilitato**.

    8. Dal **sottoscrizione** menu a discesa, fare clic su una sottoscrizione appropriata.

    9. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lasciare **reti virtuali** come **disabilitato**, se si tratta di un'opzione per l'utente.

    11. Fare clic su **Crea**.

        ![Compilandone i dettagli di archiviazione](images/AzureLabs-Lab313-37.png)

6. Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

7. Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale. Fare clic su notifiche per esplorare la nuova istanza del servizio.

    ![nuova notifica di archiviazione](images/AzureLabs-Lab313-38.png)

8. Scegliere il **Vai alla risorsa** pulsante nella notifica e verrà visualizzato la nuova pagina di panoramica di istanza del servizio di archiviazione.

    ![Vai alla risorsa](images/AzureLabs-Lab313-39.png)

9. Dalla pagina di panoramica, per il lato destro, fare clic su **tabelle**.
    
    ![Tabelle](images/AzureLabs-Lab313-40.png)

10. Il pannello sulla destra cambierà e indicherà il **servizio tabelle** informazioni, in cui è necessario aggiungere una nuova tabella. Eseguire questa operazione facendo il **+ tabella** pulsante nell'angolo superiore sinistro.

    ![Aprire le tabelle](images/AzureLabs-Lab313-41.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un **nome della tabella**. Questo è il nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi (creazione di App per le funzioni e Power BI). Inserire **IoTMessages** come nome (è possibile scegliere il proprio, è importante ricordare che quando usato più avanti in questo documento) e fare clic su **OK**. 

12. Dopo aver creata la nuova tabella, sarà possibile visualizzarlo all'interno di **servizio tabelle** (inferiore) della pagina.

    ![nuova tabella creata](images/AzureLabs-Lab313-42.png)  

13. Fare clic su **chiavi di accesso** e richiedere una copia del **nome account di archiviazione** e **chiave** (usando il blocco note), si userà questi valori più avanti in questo corso, quando si crea il **App per le funzioni di azure**.

    ![nuova tabella creata](images/AzureLabs-Lab313-43.png) 

14. Usando il pannello a sinistra, scorrere fino al *servizio tabelle* sezione e fare clic su **tabelle** (o **Sfoglia tabelle**, nei portali più recente) e richiedere una copia il  **URL di tabella** (usando il blocco note). Si userà questo valore più avanti in questo corso, quando si collegano la tabella per il **Power BI** dell'applicazione.

    ![nuova tabella creata](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capitolo 12 - tabella di Azure di completamento

Ora che il **servizio tabelle** account di archiviazione è stata configurata, è possibile aggiungere dati a esso, che verrà usato per archiviare e recuperare informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1. Aprire **Visual Studio** (**non** Visual Studio Code).

2. Dal menu, fare clic su **View** > **Cloud Explorer**.

    ![Aprire cloud explorer](images/AzureLabs-Lab313-45.png)

3. Il **Cloud Explorer** verranno aperte come un elemento ancoraggio (essere paziente, come il caricamento potrebbe richiedere tempo).

    > [!WARNING] 
    > Se la sottoscrizione è stata usata per creare le *gli account di archiviazione* non è visibile, assicurarsi di avere: 
    > - Per lo stesso account come quello usato per il portale di Azure connesso.
    > - Selezionare la sottoscrizione dalla pagina di gestione di Account (potrebbe essere necessario applicare un filtro da impostazioni dell'account):  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab313-46.png)

4. Verranno visualizzati i servizi cloud di Azure. Trovare **gli account di archiviazione** e fare clic sulla freccia a sinistra di tale per espandere l'account.

    ![Aprire l'account di archiviazione](images/AzureLabs-Lab313-47.png)

5. Una volta espanso, appena creato **account di archiviazione** devono essere disponibili. Fare clic sulla freccia a sinistra della risorsa di archiviazione e quindi una volta che viene espanso, individuare **tabelle** e fare clic sulla freccia accanto a cui, per visualizzare i **tabella** creato nel capitolo precedente. Fare doppio clic sui **tabella**.

6. La tabella verrà aperta al centro della finestra di Visual Studio. Fare clic sull'icona di tabella con il **+** (più) su di esso.

    ![Aggiungi nuova tabella](images/AzureLabs-Lab313-48.png)

7. Verrà visualizzata richiede una finestra per poter *Aggiungi entità*. Verrà creata solo un'entità, anche se hanno tre proprietà. Si noterà che *PartitionKey* e *RowKey* già disponibili, poiché verranno usati per trovare i dati dalla tabella. 

    ![chiave di partizione e di riga](images/AzureLabs-Lab313-49.png)

8. Aggiornare i valori seguenti:

    - Nome: **PartitionKey**, Value: **PK_IoTMessages** 

    - Nome: **RowKey**, valore: **RK_1_IoTMessages** 

9. Quindi, fare clic su **Aggiungi proprietà** (in basso a sinistra del *Aggiungi entità* finestra) e aggiungere la proprietà seguente:

    - **L'elemento MessageContent**, come un *stringa*, lasciare vuoto il valore.

10. La tabella deve corrispondere a quello nell'immagine seguente:

    ![aggiungere i valori corretti](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Il motivo per cui l'entità contiene il numero 1 nella chiave di riga, è perché si potrebbe voler aggiungere altri messaggi, si necessita di sperimentare ulteriormente con questo corso.

11. Fare clic su **OK** al termine. La tabella è ora pronta per essere usato.

## <a name="chapter-13---create-an-azure-function-app"></a>Capitolo 13 - creare un'App per le funzioni di Azure 

È ora possibile creare un *App per le funzioni*, che verrà chiamato dal *servizio Hub IoT* per archiviare il *IoT Edge* dispositivo i messaggi nel **tabella** Servizio che è stato creato nel capitolo precedente.

In primo luogo, è necessario creare un file che consentirà la funzione di Azure caricare le librerie che necessarie.

1.  Open **Notepad** (premere il *chiave di Windows*e il tipo *blocco note*).

    ![Aprire Blocco note](images/AzureLabs-Lab313-51.png)

2.  Aprire Blocco note, inserire la struttura JSON seguente al suo interno. Una volta che è stato fatto che, salvarlo sul desktop come **Project. JSON**. Questo file definisce le librerie che userà la funzione. Se si usa NuGet, avrà un aspetto familiare.
    
    > [!WARNING]
    > È importante che la denominazione sia corretta. Verificare che avviene **non è un file con estensione txt** estensione di file. Per riferimento, vedere di seguito:
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

3.  Accedi per il [portale di Azure](https://portal.azure.com).

4.  Una volta connessi, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **App per le funzioni**, premere il **invio** chiave, eseguire la ricerca. Fare clic su *App per le funzioni* dai risultati, aprire un nuovo pannello.

    ![cercare app per le funzioni](images/AzureLabs-Lab313-53.png)

5.  Nel nuovo pannello fornirà una descrizione del **App per le funzioni** servizio. AT nella parte inferiore sinistra del pannello, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.

    ![istanza dell'app (funzione)](images/AzureLabs-Lab313-54.png)

6.  Dopo avere fatto clic su **Create**, compilare i campi seguenti:

    1. Per la **nome App**, inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una **sottoscrizione**.

    3. Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un **servizio App di funzione**, un livello gratuito deve essere disponibile all'utente.

    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Per la **OS**, fare clic su Windows, che è la piattaforma desiderata.

    6. Selezionare una **piano di Hosting** (questa esercitazione Usa un **piano a consumo**.

    7. Selezionare una **posizione** (scegliere la stessa ubicazione come risorsa di archiviazione che hanno creato nel passaggio precedente)

    8. Per il **memorizzazione** sezione **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.

    9. Non è necessario *Application Insights* in questa app, è possibile lasciarlo **Off**.

    10. Fare clic su **Crea**.

        ![creare una nuova istanza](images/AzureLabs-Lab313-55.png)

7.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

8.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica](images/AzureLabs-Lab313-56.png)

9.  Fare clic sulla notifica, dopo la distribuzione ha esito positivo (terminata).

10. Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. 

    ![Vai alla risorsa](images/AzureLabs-Lab313-57.png)

11. Sul lato sinistro del pannello nuovo, fare clic sui **+** (più) icona accanto a *funzioni*, per creare una nuova funzione.

    ![Aggiungi nuova funzione](images/AzureLabs-Lab313-58.png)

12. All'interno del pannello centrale, il **funzione** verrà visualizzata la finestra di creazione. Scorrere ulteriormente verso il basso e fare clic su **funzione personalizzata**.

    ![funzione personalizzata](images/AzureLabs-Lab313-59.png)

13. Scorrere verso il basso la pagina successiva, fino a individuare **IoT Hub (Hub eventi)** , quindi fare clic su di esso.

    ![funzione personalizzata](images/AzureLabs-Lab313-60.png)

14. Nel **IoT Hub (Hub eventi)** blade, impostare il **Language** a **C#** e quindi fare clic su **nuovo**.

    ![funzione personalizzata](images/AzureLabs-Lab313-61.png)

15. Nella finestra che verrà visualizzato, verificare che **IoT Hub** sia selezionata e il nome del *dell'IoT Hub* campo corrisponde con il nome del *servizio Hub IoT* che è necessario creato in precedenza ([nel passaggio 8, capitolo 3](#chapter-3---the-iot-hub-service)). Scegliere il **seleziona** pulsante.

    ![funzione personalizzata](images/AzureLabs-Lab313-62.png)

16. Nella **IoT Hub (Hub eventi)** pannello, fare clic su **crea**.

    ![funzione personalizzata](images/AzureLabs-Lab313-63.png)

17. Si verrà reindirizzati all'editor di funzione.

    ![funzione personalizzata](images/AzureLabs-Lab313-64.png)

18. Eliminare tutto il codice in esso e sostituirlo con quanto segue:

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

19. Modificare le variabili seguenti, in modo che corrispondano ai valori appropriati (**tabella** e **archiviazione** valori, da [passaggio 11 e 13, rispettivamente, del capitolo 11](#chapter-11---create-table-service)), che si trovano nel **Account di archiviazione**:

    - **tableName**, con il nome del **tabella** che si trova nel **Account di archiviazione**.
    - **tableURL**, con l'URL del **tabella** che si trova nel **Account di archiviazione**.
    - **storageAccountName**, con il nome del corrispondente con il nome del valore di **Account di archiviazione** nome.
    - **storageAccountKey**, con la chiave ottenuta nel servizio di archiviazione creato in precedenza.

    ![funzione personalizzata](images/AzureLabs-Lab313-65.png)

20. Con il codice, fare clic su **salvare**.

21. Successivamente, fare clic il **\<** icona (freccia), sul lato destro della pagina.

    ![funzione personalizzata](images/AzureLabs-Lab313-66.png)

22. Un pannello verrà diapositiva da destra. In questo pannello, fare clic su **caricare**e una *Browser File* verranno visualizzati.

23. Passare a e quindi, il **Project. JSON** file, che è stato creato in **blocco note** in precedenza e quindi fare clic sui **Open** pulsante. Questo file definisce le librerie che userà la funzione.

    ![funzione personalizzata](images/AzureLabs-Lab313-67.png)

24. Quando il file è stato caricato, verrà visualizzato nel pannello a destra. Clic su di esso verrà aperta all'interno di **funzione** editor. È necessario ottenere **esattamente** quello utilizzato per l'immagine successiva.

    ![funzione personalizzata](images/AzureLabs-Lab313-68.png)

25. A questo punto può essere opportuno testare la funzionalità della funzione per memorizzare il messaggio nel *tabella*. In alto a destra della finestra, fare clic su **Test**.

    ![funzione personalizzata](images/AzureLabs-Lab313-69.png)

26. Inserire un messaggio sul **corpo della richiesta**, come illustrato nell'immagine precedente e fare clic su **eseguire**. 

27. Verrà eseguita la funzione, visualizzare lo stato dei risultati (si noterà verde **lo stato 202-accettato**sopra il *Output* finestra, il che significa è stata una chiamata riuscita):

    ![risultato dell'output](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capitolo 14 - visualizzare i messaggi attivi

Se si apre ora Visual Studio (**non** Visual Studio Code), è possibile visualizzare il risultato messaggio di test, come verrà archiviato nel *l'elemento MessageContent* stringa area.

![funzione personalizzata](images/AzureLabs-Lab313-71.png)

Con il servizio tabelle e l'App per le funzioni posto, i messaggi da dispositivo Ubuntu saranno visualizzato nei *IoTMessages* tabella. Se non è già in esecuzione, avviare nuovamente il dispositivo e sarà possibile visualizzare i messaggi risultati dal dispositivo e modulo, all'interno della tabella, usando Visual Studio *Cloud Explorer*.

![Visualizzare i dati](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capitolo 15 - il programma di installazione di Power BI

Per visualizzare i dati dal dispositivo IOT configurerà **Power BI** (versione desktop), per raccogliere i dati dalle *tabella* servizio, che appena creato. Il *HoloLens* versione di Power BI userà quindi tali dati per visualizzare il risultato.

1.  Aprire il Microsoft Store in Windows 10 e cercare **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Scaricare l'applicazione. Dopo aver terminato il download, è necessario aprirlo.

3.  Accedere al *Power BI* con il **account di Microsoft 365**. Potrebbe essere reindirizzato a un browser, effettuare l'iscrizione. Una volta che si sono iscritti, tornare all'app Power BI e accedere di nuovo.

4.  Fare clic su **recupera dati** e quindi fare clic su **più...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Fare clic su **Azure**, **archiviazione tabelle di Azure**, quindi fare clic su **Connect**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Verrà richiesto di inserire le **adresa URL Tabulky** che sono stati raccolti in precedenza ([nel passaggio 13 del capitolo 11](#chapter-11---create-table-service)), durante la creazione di un servizio tabelle. Dopo aver inserito l'URL, eliminare la parte del percorso che fa riferimento alla tabella "sottocartella" (che era IoTMessages, in questo corso). Il risultato finale dovrebbe essere visualizzato nell'immagine seguente. Quindi fare clic su **OK**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Verrà richiesto di inserire le **chiave di archiviazione** annotato ([nel passaggio 11 di 11 capitolo](#chapter-11---create-table-service)) precedenti durante la creazione nell'archiviazione tabelle. Quindi fare clic su **Connect**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Oggetto **pannello Navigatore** verrà visualizzata, selezionare la casella accanto alla tabella e fare clic su **carico**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabella è stata caricata in Power BI, ma richiede una query per visualizzare i valori in esso. A tale scopo, fare doppio clic sul nome della tabella che si trova nel **pannello campi** sul lato destro dello schermo. Quindi fare clic su **modifica Query**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Oggetto **Editor di Power Query** , verrà visualizzato come una nuova finestra di visualizzazione tabella. Fare clic sulla parola **Record** all'interno di *contenuto* colonna della tabella, per visualizzare il contenuto archiviato.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Fare clic su **Into Table**, in alto a sinistra della finestra. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Fare clic su **Chiudi e applica**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Una volta completato il caricamento della query, all'interno di **pannello campi**, sul lato destro della schermata, selezionare le caselle corrispondenti ai parametri **Name** e **valore**, a visualizzare il **l'elemento MessageContent** il contenuto della colonna.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Fare clic sui **icona del disco blu** nella parte superiore sinistra della finestra per salvare il lavoro in una cartella di propria scelta.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. È ora possibile fare clic sul pulsante pubblica per caricare la tabella nell'area di lavoro. Quando richiesto, fare clic su **area di lavoro personale** e fare clic su *seleziona*. Attendere che venga visualizzato il risultato positivo dell'invio.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Nel capitolo successivo è HoloLens specifico. Power BI non è attualmente disponibile come applicazione coinvolgente, tuttavia, è possibile eseguire la versione desktop nel portale di realtà mista Windows (noto anche come Cliff House), tramite l'app Desktop.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capitolo 16 - i dati di Power BI Visualizza su HoloLens

1. Nella finestra di HoloLens, accedere al **Microsoft Store**, toccando la relativa icona nell'elenco delle applicazioni.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Eseguire la ricerca e quindi scaricare il **Power BI** dell'applicazione.

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Avviare **Power BI** dall'elenco delle applicazioni. 

4. **Power BI** potrebbe venire richiesto di eseguire l'accesso per il **account di Microsoft 365**.

5. Una volta all'interno dell'app, l'area di lavoro dovrebbe essere visualizzata per impostazione predefinita come illustrato nell'immagine seguente. Se che ciò non accada, è sufficiente fare clic sull'icona dell'area di lavoro sul lato sinistro della finestra.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Il termine applicazione dell'IoT Hub

Complimenti, è stato creato un servizio di Hub IoT, con un dispositivo simulato Edge di macchina virtuale. Il dispositivo può comunicare i risultati di un modello di machine learning per un servizio, tabelle di Azure fornita da un'App di funzione di Azure, che viene letto in Power BI e visualizzati all'interno di un Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Espandere la struttura di messaggistica archiviata nella tabella e la visualizza sotto forma di grafico. È possibile raccogliere più dati e archiviarlo nella stessa tabella, deve essere visualizzato in un secondo momento.

### <a name="exercise-2"></a>Esercizio 2

Creare un altro modulo "acquisizione con fotocamera" da distribuire nella bacheca IoT, in modo che consente di acquisire immagini tramite la fotocamera da analizzare.
