---
title: Documentazione del pacchetto di dati spaziali della realtà mista
description: Documentazione per l'uso di pacchetti di dati spaziali di realtà mista
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager. exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539683"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentazione del pacchetto di dati spaziali della realtà mista

>[!NOTE]
> Questo strumento e le relative operazioni sono offerti così come sono. È soggetta a modifiche senza preavviso e potrebbe non essere compatibile con le versioni future di Windows o Windows Mixed Reality HMD.

## <a name="download"></a>Scarica
 Scarica [MixedRealitySpatialDataPackager qui](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Pacchetto di dati spaziali della realtà mista</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>QuickStart

Lo strumento di combinazione dei dati spaziali della realtà mista copia i dati spaziali di un'app di destinazione da un PC a un altro tramite un processo di esportazione e importazione in due passaggi. Lo strumento deve essere eseguito con privilegi di amministratore ed Elimina i dati spaziali esistenti durante l'importazione. L'esportazione lascia intatti i dati spaziali esistenti.

Requisiti e limitazioni principali:

1. Lo strumento deve essere eseguito con privilegi di amministratore 
2. Potrebbe essere necessario riavviare il computer se il portale per la realtà mista è instabile dopo l'esecuzione dello strumento
3. Lo strumento non verrà eseguito in caso di mancata corrispondenza delle versioni dei dati spaziali o di incompatibilità
4. Lo strumento cancellerà i dati spaziali esistenti durante l'importazione
5. Se il processo di importazione ha esito negativo, non è possibile ripristinare i dati precedenti a meno che non sia stato eseguito il backup esportando precedentemente
6. Funzionalità di importazione di qualità che condizionano la modalità di "sola lettura" per i dati della mappa spaziale
***

## <a name="mapping-best-practices"></a>Procedure consigliate per il mapping

1. Cancellare le mappe esistenti dal pannello di controllo (Impostazioni-> realtà mista-> ambiente-> cancellare i dati dell'ambiente)
2. Assicurarsi che l'illuminazione sia sufficiente per un corretto rilevamento e se l'esecuzione della modalità Mappa bloccata tenti di mantenere la stessa illuminazione
3. Quando possibile, evitare di ridurre l'intervallo dinamico di illuminazione evitando aree di illuminazione elevata accanto a aree ombreggiate scure
4. Ridurre al minimo le superfici senza trama, ad esempio inserire un intervallo di poster diversi sui muri bianchi
5. Mappare lo spazio senza oggetti dinamici nella scena, ad esempio lo stato di trasferimento di persone
6. Blocca la mappa durante l'importazione (disponibile tramite l'anteprima di Insider)
7. Sbloccare la mappa e ripetere l'analisi dell'ambiente quando si verificano peggioramenti della qualità e/o sono presenti modifiche nell'ambiente (illuminazione o modifiche nel layout degli oggetti)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Esecuzione di pacchetti di dati spaziali di realtà mista con script complementare

È stato fornito MRSpatialPackagerHelperScript. ps1 che esegue gli strumenti della mappa di pacchetti. 


I parametri dello script sono definiti di seguito:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Esempio di utilizzo e output di script di PowerShell

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName Administrator-mode Export-MapxPath D:\temp\-LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Come esportare con MixedRealityPackager. exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

L'esportazione delle mappe dal dispositivo genera due file MapX, het. MapX e sa. MapX. Durante il processo di esportazione tutti gli ancoraggi spaziali vengono rimossi tranne l'app specificata e il limite creato dall'utente (se esistente). Il nome della famiglia di pacchetti di origine deve corrispondere a un'app installata esistente o il file exe non riuscirà.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Come importare con MixedRealityPackager. exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
L'importazione Elimina i dati spaziali esistenti e li sostituisce con i dati della directory specificata. L'input del nome dell'app specifica il nome del pacchetto dell'app di destinazione per cui devono essere importati gli ancoraggi spaziali e il SID utente di destinazione specifica l'utente che deve avere accesso agli ancoraggi spaziali importati. Il nome della famiglia di pacchetti di destinazione e i SID utente devono corrispondere ai valori esistenti nel PC oppure il file exe avrà esito negativo.


***
## <a name="error-messages"></a>Messaggi di errore
Inoltre, i messaggi di errore che seguono gli errori saranno associati a un HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Se si è verificato un errore di argomenti non validi
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Se il file eseguibile non è stato eseguito in modalità amministratore
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Se si è verificato un errore durante l'abilitazione o la disabilitazione del driver
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Se si è verificato un errore durante la convalida della versione del database spaziale
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Se si è verificato un errore durante la convalida del nome della famiglia di pacchetti fornito per l'app di importazione/esportazione di destinazione
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Se si è verificato un errore durante la convalida del SID utente
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Se si è verificato un errore relativo ai file di dati spaziali di origine o di destinazione
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Se si è verificato un errore relativo all'avvio e all'arresto dello spettro/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
