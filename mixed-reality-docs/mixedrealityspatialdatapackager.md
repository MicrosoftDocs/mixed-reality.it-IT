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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="b2590-104">Documentazione Packager di dati spaziali di realtà mista</span><span class="sxs-lookup"><span data-stu-id="b2590-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="b2590-105">Questo strumento e il suo funzionamento sono disponibili come-è.</span><span class="sxs-lookup"><span data-stu-id="b2590-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="b2590-106">È soggetto a modifiche senza alcun preavviso e potrebbero non essere compatibile con Windows futuri o rilascia HMD realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="b2590-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="b2590-107">Scarica</span><span class="sxs-lookup"><span data-stu-id="b2590-107">Download</span></span>
 <span data-ttu-id="b2590-108">Scaricare [MixedRealitySpatialDataPackager qui](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="b2590-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="b2590-109">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="b2590-109">Quickstart</span></span>

<span data-ttu-id="b2590-110">Lo strumento di realtà mista, Packager spaziali dati copiati i dati spaziali di un'app di destinazione da un computer a un altro tramite un passaggio due esportare e importare processo.</span><span class="sxs-lookup"><span data-stu-id="b2590-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="b2590-111">Lo strumento deve essere eseguito con privilegi di amministratore ed elimina i dati spaziali esistenti al momento dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="b2590-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="b2590-112">Esportazione lascia intatti i dati spaziali esistenti.</span><span class="sxs-lookup"><span data-stu-id="b2590-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="b2590-113">Requisiti e limitazioni:</span><span class="sxs-lookup"><span data-stu-id="b2590-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="b2590-114">Lo strumento deve essere eseguito con privilegi di amministratore</span><span class="sxs-lookup"><span data-stu-id="b2590-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="b2590-115">Potrebbe essere necessario riavviare il PC se il portale di realtà mista è instabile dopo aver eseguito lo strumento</span><span class="sxs-lookup"><span data-stu-id="b2590-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="b2590-116">Lo strumento non verrà eseguito quando si verificano mancate corrispondenze di versione dei dati spaziali o le incompatibilità</span><span class="sxs-lookup"><span data-stu-id="b2590-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="b2590-117">Strumento cancellerà i dati spaziali esistenti al momento dell'importazione</span><span class="sxs-lookup"><span data-stu-id="b2590-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="b2590-118">Se il processo di importazione non riesce precedente non è possibile ripristinare i dati a meno che non lo è stato eseguito il tramite l'esportazione in precedenza</span><span class="sxs-lookup"><span data-stu-id="b2590-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="b2590-119">Qualità della funzionalità di importazione condizionate alla "modalità sola"lettura per i dati spaziali della mappa</span><span class="sxs-lookup"><span data-stu-id="b2590-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="b2590-120">Le procedure consigliate di mapping</span><span class="sxs-lookup"><span data-stu-id="b2590-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="b2590-121">Deselezionare i mapping esistenti dal Pannello di controllo (Impostazioni -> realtà mista -> ambiente -> dati dell'ambiente non crittografato)</span><span class="sxs-lookup"><span data-stu-id="b2590-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="b2590-122">Assicurarsi di illuminazione sufficienti per il rilevamento valida e se in esecuzione in modalità mappa bloccato provare a mantenere la stessa illuminazione</span><span class="sxs-lookup"><span data-stu-id="b2590-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="b2590-123">Quando è possibile mantenere l'intervallo dinamico di illuminazione ridotto, evitando le aree di illuminazione alto accanto ad aree nascoste, scure</span><span class="sxs-lookup"><span data-stu-id="b2590-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="b2590-124">Ridurre al minimo vuoto, superfici textureless inserire, ad esempio un intervallo di poster diversi sui muri bianchi</span><span class="sxs-lookup"><span data-stu-id="b2590-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="b2590-125">Eseguire il mapping di spazio senza oggetti dinamici nella scena, come lo spostamento di utenti</span><span class="sxs-lookup"><span data-stu-id="b2590-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="b2590-126">Bloccare la mappa al momento dell'importazione (disponibile tramite Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="b2590-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="b2590-127">Sbloccare la mappa e ripetere l'analisi di ambiente quando il rilevamento della qualità comporta una riduzione e/o sono state apportate modifiche nell'ambiente (illuminazione o le modifiche nel layout degli oggetti)</span><span class="sxs-lookup"><span data-stu-id="b2590-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="b2590-128">In esecuzione Packager di dati spaziali di realtà mista con Script complementare</span><span class="sxs-lookup"><span data-stu-id="b2590-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="b2590-129">Sono state fornite MRSpatialPackagerHelperScript.ps1 che esegue il packager mappa gli strumenti.</span><span class="sxs-lookup"><span data-stu-id="b2590-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="b2590-130">I parametri dello script sono definiti di seguito:</span><span class="sxs-lookup"><span data-stu-id="b2590-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="b2590-131">Output e l'utilizzo di esempio di Script di Powershell</span><span class="sxs-lookup"><span data-stu-id="b2590-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="b2590-132">.\MRSpatialPackagerHelperScript.ps1 - AppName holoshell - nome utente amministratore-modalità di esportazione - MapxPath D:\temp\ - LockMap 0</span><span class="sxs-lookup"><span data-stu-id="b2590-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="b2590-133">Procedura esportazione mediante MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="b2590-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="b2590-134">L'esportazione di mappe su un dispositivo offline genera due file mapx, het.mapx e sa.mapx.</span><span class="sxs-lookup"><span data-stu-id="b2590-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="b2590-135">Durante il processo di esportazione tutti i punti di ancoraggio spaziali vengono rimossi fatta eccezione per l'app specificata e il limite creato dall'utente (se presente).</span><span class="sxs-lookup"><span data-stu-id="b2590-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="b2590-136">Il nome di famiglia di pacchetti di origine deve corrispondere a un'app installata esistente o il file exe avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="b2590-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="b2590-137">Come importare usando MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="b2590-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="b2590-138">Importazione consente di eliminare i dati spaziali esistenti e lo sostituisce con i dati della directory specificata.</span><span class="sxs-lookup"><span data-stu-id="b2590-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="b2590-139">L'input di nome di app consente di specificare il nome del pacchetto dell'app di destinazione che desidera che gli ancoraggi spaziali deve essere importato per e il SID utente di destinazione specifica l'utente che dispone accedere ai punti di ancoraggio spaziali importati.</span><span class="sxs-lookup"><span data-stu-id="b2590-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="b2590-140">Il nome famiglia pacchetto di destinazione e il SID dell'utente devono corrispondere ai valori esistenti in un computer o il file exe avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="b2590-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="b2590-141">Messaggi di errore</span><span class="sxs-lookup"><span data-stu-id="b2590-141">Error Messages</span></span>
<span data-ttu-id="b2590-142">Inoltre i messaggi di errore seguito errori anche sia associati a un HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2590-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="b2590-143">Se si è verificato un errore argomenti non validi</span><span class="sxs-lookup"><span data-stu-id="b2590-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="b2590-144">Se il file eseguibile non è stato eseguito in modalità amministratore</span><span class="sxs-lookup"><span data-stu-id="b2590-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="b2590-145">Se si è verificato un errore, abilitare o disabilitare il driver</span><span class="sxs-lookup"><span data-stu-id="b2590-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="b2590-146">Se si è verificato un errore durante la convalida la versione del database spaziali</span><span class="sxs-lookup"><span data-stu-id="b2590-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="b2590-147">Se si è verificato un errore di convalida del nome famiglia pacchetto fornito per l'app di importazione/esportazione di destinazione</span><span class="sxs-lookup"><span data-stu-id="b2590-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="b2590-148">Se si è verificato un errore durante la convalida il SID utente</span><span class="sxs-lookup"><span data-stu-id="b2590-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="b2590-149">Se si è verificato un errore per i dati spaziali di origine o destinazione file correlati</span><span class="sxs-lookup"><span data-stu-id="b2590-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="b2590-150">Se si è verificato un errore relativo all'avvio e arresto spettro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="b2590-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
