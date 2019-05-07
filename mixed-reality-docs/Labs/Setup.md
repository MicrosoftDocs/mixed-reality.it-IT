# <a name="setting-up"></a>Configurazione di

Guida introduttiva con l'API di Azure Kinect DK? Ricerca è finita! Questo documento otterrà è attivo e in esecuzione con l'accesso al dispositivo.

Prima di tutto, scaricare e installare il [API di Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) da Github.

**Contenuto**  
[Intestazioni](#Headers)  
[Ricerca di un dispositivo Kinect](#Finding-a-Kinect-Device)  
[Avviare le videocamere](#Starting-the-Cameras)  
[Gestione degli errori](#Error-Handling)  
[Codice sorgente completo](#Full-Source)  

**Di seguito sono le funzioni che si userà:**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>Intestazioni
È presente solo un'intestazione che è necessario e che è k4a.h! Assicurarsi che il compilatore di scelta è configurato con lib del SDK e includere le cartelle. È necessario anche i file k4a.lib e k4a.dll collegati.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Ricerca di un dispositivo Kinect

![](img/Serial.png)

Più dispositivi DK Kinect Azure possono essere connessi al computer in uso. Si inizierà innanzitutto dalla ricerca out quanti, o se sono connesse tramite il [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) (funzione). Questa funzione dovrebbe funzionare immediatamente, senza alcuna configurazione aggiuntiva.

```C
uint32_t count = k4a_device_get_installed_count();
```

Dopo aver stabilito vi è effettivamente un dispositivo connesso al computer, è possibile aprirlo utilizzando [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open). È possibile fornire l'indice del dispositivo che si desidera aprire, oppure è possibile usare semplicemente [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) per il primo.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
Come con la maggior parte delle operazioni nell'API k4a, quando si apre un file, è necessario anche chiuderlo quando hai finito con esso. Quando è in corso l'arresto, ricordarsi di effettuare una chiamata a [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).

```C
k4a_device_close(device);
```

Dopo aver aperto il dispositivo, è possibile inviare un test di un'operazione estremamente semplice per assicurarsi che sia tutto a posto. Pertanto, è possibile leggere il numero di serie del dispositivo.

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

## <a name="starting-the-cameras"></a>Avviare le videocamere

Dopo aver aperto il dispositivo, è necessario configurare la fotocamera con un [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) oggetto! Configurazione della fotocamera ha un numero di opzioni diverse e sarà necessario scegliere le impostazioni che meglio si adattano allo scenario specifico.

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

Per i dettagli di configurazione sulla __colore__ fotocamera, indica [consulta questo documento]()!  
Per i dettagli di configurazione sulla __profondità__ fotocamera, indica [consulta questo documento]()!

## <a name="error-handling"></a>Gestione degli errori

Per ragioni di brevità e chiarezza, non viene visualizzato in alcuni esempi di inline di gestione degli errori. Tuttavia, la gestione degli errori è sempre importante! Molte funzioni restituirà un tipo generale di esito positivo o negativo [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), o una variante più specifica con informazioni dettagliate, ad esempio [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). Assicurarsi di controllare la documentazione o intellisense di una funzione specifica per visualizzare i messaggi di errore si aspetterebbe di vedere da quest'ultimo.

Con i tipi di errore, è inoltre disponibile il [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) e [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macro che è possibile usare con essi. Quindi, invece di aprire solo un dispositivo k4a, si potrebbe essere proteggerla simile al seguente:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>Codice sorgente completo

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>Laboratorio successivo - [la lettura dei dati di profondità](ReadDepth.md)
