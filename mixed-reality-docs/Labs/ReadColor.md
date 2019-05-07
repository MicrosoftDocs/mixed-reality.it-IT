# <a name="reading-rgb-data"></a>La lettura dei dati RGB

**Contenuto**  
[Configurazione del dispositivo](#Configuring-the-Device)  
[Recupero di un Frame di colore](#Getting-a-Color-Frame)  
[Pulizia](#Cleaning-Up)  
[Codice sorgente completo](#Full-Source)  

**Di seguito sono le funzioni che si userà:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>Configurazione del dispositivo

Dopo aver [apertura di un dispositivo k4a](), sarà necessario configurare le fotocamere per acquisire dati relativi al colore. È anche molte opzioni qui accediamo a ognuna di esse. Di seguito è riportato un esempio di ciò che sembra essere avviate da una fotocamera colore davvero di base.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

Il `color_format` ci consente di specificare come si desidera che le informazioni di colore memorizzate nel buffer di immagine. `K4A_IMAGE_FORMAT_COLOR_BGRA32` sarebbe 32 bit per pixel, archiviato come 8 bit per il blu, verde, rosso e alfa. Questo formato viene usato negli esempi a causa la comodità, ma se si desidera essere concious dell'utilizzo della memoria, gli altri formati potrebbero essere scelte di livello superiore.

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|Colore dati saranno presentati in [formato JPEG di movimento](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 dello spazio dei colori: 0 di formato, NV12, disponibile solo con risoluzione 720p.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 dello spazio dei colori: 2 Formato YUY2, disponibile solo con risoluzione 720p.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|Dati non elaborati colori, 32 bit per pixel, ordinato come blu, verde, rosso e alfa|

Durante la scrittura la propria conversione YUV può essere difficile, una libreria veloce e affidabile per conversione YUV reperibili [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).

Il `color_resolution` ha anche un paio di opzioni.

|`color_resolution`|Risoluzione|Aspetto|campo di visualizzazione| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | Frequenza dei fotogrammi massimo 15.

E ovviamente il `camera_fps` anche.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>Recupero di un Frame di colore

Recupero dei dati per un intervallo di colori e un frame di profondità è una procedura molto simile. Prima di tutto è ottenere un'acquisizione dal dispositivo, quindi vengono estratte le immagini a colori da quest'ultimo e quindi è estrarre i dati non elaborati da tale immagine.

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

I dati archiviati in `colorDataBRGA` dipende dal formato è indicati nella configurazione. Poiché si è richiesto `K4A_IMAGE_FORMAT_COLOR_BGRA32`, abbiamo una matrice di valori di colori a 32 bit archiviati in BGRA order!

In questo caso, i file TGA archiviano colori nell'ordine BGR già! E poiché la funzione di salvataggio è possibile ignorare il canale alfa con questi argomenti, è possibile passare solo i dati dell'immagine è!

## <a name="cleaning-up"></a>Pulizia

E come sempre, ricordarsi di rilasciare le risorse al termine con loro!
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>Codice sorgente completo

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>Laboratorio successivo - [combinazione colori e i dati di profondità](MixDepthAndRGB.md)