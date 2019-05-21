---
title: Documentazione Packager di dati spaziali di realtà mista
description: Documentazione per l'uso di realtà mista, Packager spaziali dati
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942107"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentazione Packager di dati spaziali di realtà mista

>[!NOTE]
> Questo strumento e il suo funzionamento sono disponibili come-è. È soggetto a modifiche senza alcun preavviso e potrebbero non essere compatibile con Windows futuri o rilascia HMD realtà mista di Windows.

## <a name="download"></a>Scarica
 Scaricare [MixedRealitySpatialDataPackager qui](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>Guida introduttiva

Lo strumento di realtà mista, Packager spaziali dati copiati i dati spaziali di un'app di destinazione da un computer a un altro tramite un passaggio due esportare e importare processo. Lo strumento deve essere eseguito con privilegi di amministratore ed elimina i dati spaziali esistenti al momento dell'importazione. Esportazione lascia intatti i dati spaziali esistenti.

Requisiti e limitazioni:

1. Lo strumento deve essere eseguito con privilegi di amministratore 
2. Potrebbe essere necessario riavviare il PC se il portale di realtà mista è instabile dopo aver eseguito lo strumento
3. Lo strumento non verrà eseguito quando si verificano mancate corrispondenze di versione dei dati spaziali o le incompatibilità
4. Strumento cancellerà i dati spaziali esistenti al momento dell'importazione
5. Se il processo di importazione non riesce precedente non è possibile ripristinare i dati a meno che non lo è stato eseguito il tramite l'esportazione in precedenza
6. Qualità della funzionalità di importazione condizionate alla "modalità sola"lettura per i dati spaziali della mappa
***

## <a name="mapping-best-practices"></a>Le procedure consigliate di mapping

1. Deselezionare i mapping esistenti dal Pannello di controllo (Impostazioni -> realtà mista -> ambiente -> dati dell'ambiente non crittografato)
2. Assicurarsi di illuminazione sufficienti per il rilevamento valida e se in esecuzione in modalità mappa bloccato provare a mantenere la stessa illuminazione
3. Quando è possibile mantenere l'intervallo dinamico di illuminazione ridotto, evitando le aree di illuminazione alto accanto ad aree nascoste, scure
4. Ridurre al minimo vuoto, superfici textureless inserire, ad esempio un intervallo di poster diversi sui muri bianchi
5. Eseguire il mapping di spazio senza oggetti dinamici nella scena, come lo spostamento di utenti
6. Bloccare la mappa al momento dell'importazione (disponibile tramite Insider Preview)
7. Sbloccare la mappa e ripetere l'analisi di ambiente quando il rilevamento della qualità comporta una riduzione e/o sono state apportate modifiche nell'ambiente (illuminazione o le modifiche nel layout degli oggetti)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>In esecuzione Packager di dati spaziali di realtà mista con Script complementare

Sono state fornite MRSpatialPackagerHelperScript.ps1 che esegue il packager mappa gli strumenti. 


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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Output e l'utilizzo di esempio di Script di Powershell

.\MRSpatialPackagerHelperScript.ps1 - AppName holoshell - nome utente amministratore-modalità di esportazione - MapxPath D:\temp\ - LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Procedura esportazione mediante MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

L'esportazione di mappe su un dispositivo offline genera due file mapx, het.mapx e sa.mapx. Durante il processo di esportazione tutti i punti di ancoraggio spaziali vengono rimossi fatta eccezione per l'app specificata e il limite creato dall'utente (se presente). Il nome di famiglia di pacchetti di origine deve corrispondere a un'app installata esistente o il file exe avrà esito negativo.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Come importare usando MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Importazione consente di eliminare i dati spaziali esistenti e lo sostituisce con i dati della directory specificata. L'input di nome di app consente di specificare il nome del pacchetto dell'app di destinazione che desidera che gli ancoraggi spaziali deve essere importato per e il SID utente di destinazione specifica l'utente che dispone accedere ai punti di ancoraggio spaziali importati. Il nome famiglia pacchetto di destinazione e il SID dell'utente devono corrispondere ai valori esistenti in un computer o il file exe avrà esito negativo.


***
## <a name="error-messages"></a>Messaggi di errore
Inoltre i messaggi di errore seguito errori anche sia associati a un HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Se si è verificato un errore argomenti non validi
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Se il file eseguibile non è stato eseguito in modalità amministratore
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Se si è verificato un errore, abilitare o disabilitare il driver
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Se si è verificato un errore durante la convalida la versione del database spaziali
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Se si è verificato un errore di convalida del nome famiglia pacchetto fornito per l'app di importazione/esportazione di destinazione
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Se si è verificato un errore durante la convalida il SID utente
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Se si è verificato un errore per i dati spaziali di origine o destinazione file correlati
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Se si è verificato un errore relativo all'avvio e arresto spettro/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
