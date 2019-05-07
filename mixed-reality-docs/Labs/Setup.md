# <a name="setting-up"></a><span data-ttu-id="36e65-101">Configurazione di</span><span class="sxs-lookup"><span data-stu-id="36e65-101">Setting Up</span></span>

<span data-ttu-id="36e65-102">Guida introduttiva con l'API di Azure Kinect DK?</span><span class="sxs-lookup"><span data-stu-id="36e65-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="36e65-103">Ricerca è finita!</span><span class="sxs-lookup"><span data-stu-id="36e65-103">Look no further!</span></span> <span data-ttu-id="36e65-104">Questo documento otterrà è attivo e in esecuzione con l'accesso al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="36e65-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="36e65-105">Prima di tutto, scaricare e installare il [API di Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) da Github.</span><span class="sxs-lookup"><span data-stu-id="36e65-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="36e65-106">**Contenuto**</span><span class="sxs-lookup"><span data-stu-id="36e65-106">**Contents**</span></span>  
[<span data-ttu-id="36e65-107">Intestazioni</span><span class="sxs-lookup"><span data-stu-id="36e65-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="36e65-108">Ricerca di un dispositivo Kinect</span><span class="sxs-lookup"><span data-stu-id="36e65-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="36e65-109">Avviare le videocamere</span><span class="sxs-lookup"><span data-stu-id="36e65-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="36e65-110">Gestione degli errori</span><span class="sxs-lookup"><span data-stu-id="36e65-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="36e65-111">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="36e65-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="36e65-112">**Di seguito sono le funzioni che si userà:**</span><span class="sxs-lookup"><span data-stu-id="36e65-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="36e65-113">Intestazioni</span><span class="sxs-lookup"><span data-stu-id="36e65-113">Headers</span></span>
<span data-ttu-id="36e65-114">È presente solo un'intestazione che è necessario e che è k4a.h!</span><span class="sxs-lookup"><span data-stu-id="36e65-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="36e65-115">Assicurarsi che il compilatore di scelta è configurato con lib del SDK e includere le cartelle.</span><span class="sxs-lookup"><span data-stu-id="36e65-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="36e65-116">È necessario anche i file k4a.lib e k4a.dll collegati.</span><span class="sxs-lookup"><span data-stu-id="36e65-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="36e65-117">Ricerca di un dispositivo Kinect</span><span class="sxs-lookup"><span data-stu-id="36e65-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="36e65-118">Più dispositivi DK Kinect Azure possono essere connessi al computer in uso.</span><span class="sxs-lookup"><span data-stu-id="36e65-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="36e65-119">Si inizierà innanzitutto dalla ricerca out quanti, o se sono connesse tramite il [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) (funzione).</span><span class="sxs-lookup"><span data-stu-id="36e65-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="36e65-120">Questa funzione dovrebbe funzionare immediatamente, senza alcuna configurazione aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="36e65-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="36e65-121">Dopo aver stabilito vi è effettivamente un dispositivo connesso al computer, è possibile aprirlo utilizzando [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span><span class="sxs-lookup"><span data-stu-id="36e65-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="36e65-122">È possibile fornire l'indice del dispositivo che si desidera aprire, oppure è possibile usare semplicemente [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) per il primo.</span><span class="sxs-lookup"><span data-stu-id="36e65-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="36e65-123">Come con la maggior parte delle operazioni nell'API k4a, quando si apre un file, è necessario anche chiuderlo quando hai finito con esso.</span><span class="sxs-lookup"><span data-stu-id="36e65-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="36e65-124">Quando è in corso l'arresto, ricordarsi di effettuare una chiamata a [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span><span class="sxs-lookup"><span data-stu-id="36e65-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="36e65-125">Dopo aver aperto il dispositivo, è possibile inviare un test di un'operazione estremamente semplice per assicurarsi che sia tutto a posto.</span><span class="sxs-lookup"><span data-stu-id="36e65-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="36e65-126">Pertanto, è possibile leggere il numero di serie del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="36e65-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="36e65-127">Avviare le videocamere</span><span class="sxs-lookup"><span data-stu-id="36e65-127">Starting the Cameras</span></span>

<span data-ttu-id="36e65-128">Dopo aver aperto il dispositivo, è necessario configurare la fotocamera con un [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) oggetto!</span><span class="sxs-lookup"><span data-stu-id="36e65-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="36e65-129">Configurazione della fotocamera ha un numero di opzioni diverse e sarà necessario scegliere le impostazioni che meglio si adattano allo scenario specifico.</span><span class="sxs-lookup"><span data-stu-id="36e65-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="36e65-130">Per i dettagli di configurazione sulla __colore__ fotocamera, indica [consulta questo documento]()!</span><span class="sxs-lookup"><span data-stu-id="36e65-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="36e65-131">Per i dettagli di configurazione sulla __profondità__ fotocamera, indica [consulta questo documento]()!</span><span class="sxs-lookup"><span data-stu-id="36e65-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="36e65-132">Gestione degli errori</span><span class="sxs-lookup"><span data-stu-id="36e65-132">Error Handling</span></span>

<span data-ttu-id="36e65-133">Per ragioni di brevità e chiarezza, non viene visualizzato in alcuni esempi di inline di gestione degli errori.</span><span class="sxs-lookup"><span data-stu-id="36e65-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="36e65-134">Tuttavia, la gestione degli errori è sempre importante!</span><span class="sxs-lookup"><span data-stu-id="36e65-134">However, error handling is always important!</span></span> <span data-ttu-id="36e65-135">Molte funzioni restituirà un tipo generale di esito positivo o negativo [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), o una variante più specifica con informazioni dettagliate, ad esempio [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span><span class="sxs-lookup"><span data-stu-id="36e65-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="36e65-136">Assicurarsi di controllare la documentazione o intellisense di una funzione specifica per visualizzare i messaggi di errore si aspetterebbe di vedere da quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="36e65-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="36e65-137">Con i tipi di errore, è inoltre disponibile il [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) e [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macro che è possibile usare con essi.</span><span class="sxs-lookup"><span data-stu-id="36e65-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="36e65-138">Quindi, invece di aprire solo un dispositivo k4a, si potrebbe essere proteggerla simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="36e65-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="36e65-139">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="36e65-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="36e65-140">Laboratorio successivo - [la lettura dei dati di profondità](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="36e65-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
