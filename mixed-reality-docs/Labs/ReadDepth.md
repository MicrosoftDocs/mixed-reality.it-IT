# <a name="reading-depth-data"></a>La lettura dei dati di profondità

Necessario leggere i dati di profondità dal dispositivo? È facile!

**Contenuto**  
[Configurazione del dispositivo](#Configuring-the-Device)  
[Profondità di accesso ai dati](#Acessing-Depth-Data)  
[Pulizia](#Cleaning-Up)  
[Codice sorgente completo](#Full-Source)  

**Di seguito sono le funzioni che si userà:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>Configurazione del dispositivo

Dopo aver [aprendo un'interfaccia]() al dispositivo di Azure Kinect DK, è necessario configurare la fotocamera per acquisire i dati di profondità. È presente solo un elemento è strettamente necessario conoscerne su durante la configurazione di profondità, ecco il `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

In questo caso il `depth_mode` offre due opzioni. A seconda del contesto dell'applicazione, è possibile richiedere i dati di profondità in formati diversi.

Si eseguono algoritmi time vincolata sui dati di profondità? Selezionare una modalità 2X2BINNED ad esempio in modo che non ci sono meno dati su cui operare. È importante più ciò che è di gran lunga out direttamente ahead, piuttosto che cosa è vicino e nella periferia? Usare un campo di visualizzazione ridotta con le modalità NFOV!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|Angolo ampia visualizzazione (almeno 120 x 120), profondità superficiale (0,25-2.21 m), la risoluzione dei dati elevata (1024 x 1024). Ha un frequenza fotogrammi massimo pari a 15.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|Angolo ampia visualizzazione (almeno 120 x 120), profondità superficiale (0,25-2,88 m), la risoluzione dei dati bassa (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|Angolo ristretto visualizzazione (75 x 65), profondità distante (0,5-3.86 m), la risoluzione dei dati elevata (640 x 576).|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|Angolo ristretto visualizzazione (75 x 65), profondità distante (0,5 - 5.46, lettera m), la risoluzione dei dati bassa (320 x 288).|
|`K4A_DEPTH_MODE_PASSIVE_IR`|Raw feed tra la camera e runtime di integrazione (1024 x 1024)|
||Profondità sarà disponibili di fuori intervallo indicato in base alla riflessione oggetto.|

## <a name="acessing-depth-data"></a>Profondità di accesso ai dati

![](img/Depth.png)

Quando si acquisisce un frame dal dispositivo, è possibile usare `k4a_capture_get_depth_image` e `k4a_image_get_buffer` per ottenere i dati di profondità non elaborati.

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

Informazioni più approfondite viene fornite come una matrice di interi senza segno a 16 bit, che rappresenta millimetri dalla fotocamera. La matrice conterrà zero se il valore della profondità non è presente per un particolare pixel.

In questo esempio, è semplicemente verrà convertire i dati di profondità in un'immagine in scala di grigi e salvarlo in un file.

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a>Pulizia

Ricordarsi di arrestare e rilasciare tutti gli elementi che sono state allocate o afferrato! Tenere presente che le acquisizioni di frame devono essere liberate dopo aver terminato con loro e prima di trascinare un altro frame.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>Codice sorgente completo

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a>Laboratorio successivo - [la lettura dei dati RGB](ReadColor.md)