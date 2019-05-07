# <a name="reading-rgb-data"></a><span data-ttu-id="c3d94-101">La lettura dei dati RGB</span><span class="sxs-lookup"><span data-stu-id="c3d94-101">Reading RGB Data</span></span>

<span data-ttu-id="c3d94-102">**Contenuto**</span><span class="sxs-lookup"><span data-stu-id="c3d94-102">**Contents**</span></span>  
[<span data-ttu-id="c3d94-103">Configurazione del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c3d94-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="c3d94-104">Recupero di un Frame di colore</span><span class="sxs-lookup"><span data-stu-id="c3d94-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="c3d94-105">Pulizia</span><span class="sxs-lookup"><span data-stu-id="c3d94-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="c3d94-106">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="c3d94-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="c3d94-107">**Di seguito sono le funzioni che si userà:**</span><span class="sxs-lookup"><span data-stu-id="c3d94-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="c3d94-108">Configurazione del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c3d94-108">Configuring the Device</span></span>

<span data-ttu-id="c3d94-109">Dopo aver [apertura di un dispositivo k4a](), sarà necessario configurare le fotocamere per acquisire dati relativi al colore.</span><span class="sxs-lookup"><span data-stu-id="c3d94-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="c3d94-110">È anche molte opzioni qui accediamo a ognuna di esse.</span><span class="sxs-lookup"><span data-stu-id="c3d94-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="c3d94-111">Di seguito è riportato un esempio di ciò che sembra essere avviate da una fotocamera colore davvero di base.</span><span class="sxs-lookup"><span data-stu-id="c3d94-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="c3d94-112">Il `color_format` ci consente di specificare come si desidera che le informazioni di colore memorizzate nel buffer di immagine.</span><span class="sxs-lookup"><span data-stu-id="c3d94-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="c3d94-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` sarebbe 32 bit per pixel, archiviato come 8 bit per il blu, verde, rosso e alfa.</span><span class="sxs-lookup"><span data-stu-id="c3d94-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="c3d94-114">Questo formato viene usato negli esempi a causa la comodità, ma se si desidera essere concious dell'utilizzo della memoria, gli altri formati potrebbero essere scelte di livello superiore.</span><span class="sxs-lookup"><span data-stu-id="c3d94-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="c3d94-115">Colore dati saranno presentati in [formato JPEG di movimento](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="c3d94-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="c3d94-116">[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 dello spazio dei colori: 0 di formato, NV12, disponibile solo con risoluzione 720p.</span><span class="sxs-lookup"><span data-stu-id="c3d94-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="c3d94-117">[YUV](https://en.wikipedia.org/wiki/YUV) 4:2 dello spazio dei colori: 2 Formato YUY2, disponibile solo con risoluzione 720p.</span><span class="sxs-lookup"><span data-stu-id="c3d94-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="c3d94-118">Dati non elaborati colori, 32 bit per pixel, ordinato come blu, verde, rosso e alfa</span><span class="sxs-lookup"><span data-stu-id="c3d94-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="c3d94-119">Durante la scrittura la propria conversione YUV può essere difficile, una libreria veloce e affidabile per conversione YUV reperibili [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span><span class="sxs-lookup"><span data-stu-id="c3d94-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="c3d94-120">Il `color_resolution` ha anche un paio di opzioni.</span><span class="sxs-lookup"><span data-stu-id="c3d94-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="c3d94-121">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="c3d94-121">resolution</span></span>|<span data-ttu-id="c3d94-122">Aspetto</span><span class="sxs-lookup"><span data-stu-id="c3d94-122">aspect</span></span>|<span data-ttu-id="c3d94-123">campo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="c3d94-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="c3d94-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c3d94-124">1280 x 720</span></span>  | <span data-ttu-id="c3d94-125">16:9</span><span class="sxs-lookup"><span data-stu-id="c3d94-125">16:9</span></span> | <span data-ttu-id="c3d94-126">90x59</span><span class="sxs-lookup"><span data-stu-id="c3d94-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="c3d94-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="c3d94-127">1920 x 1080</span></span> | <span data-ttu-id="c3d94-128">16:9</span><span class="sxs-lookup"><span data-stu-id="c3d94-128">16:9</span></span> | <span data-ttu-id="c3d94-129">90x59</span><span class="sxs-lookup"><span data-stu-id="c3d94-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="c3d94-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="c3d94-130">2560 x 1440</span></span> | <span data-ttu-id="c3d94-131">16:9</span><span class="sxs-lookup"><span data-stu-id="c3d94-131">16:9</span></span> | <span data-ttu-id="c3d94-132">90x59</span><span class="sxs-lookup"><span data-stu-id="c3d94-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="c3d94-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="c3d94-133">3840 x 2160</span></span> | <span data-ttu-id="c3d94-134">16:9</span><span class="sxs-lookup"><span data-stu-id="c3d94-134">16:9</span></span> | <span data-ttu-id="c3d94-135">90x59</span><span class="sxs-lookup"><span data-stu-id="c3d94-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="c3d94-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="c3d94-136">2048 x 1536</span></span> | <span data-ttu-id="c3d94-137">4:3</span><span class="sxs-lookup"><span data-stu-id="c3d94-137">4:3</span></span>  | <span data-ttu-id="c3d94-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="c3d94-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="c3d94-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="c3d94-139">4096 x 3072</span></span> | <span data-ttu-id="c3d94-140">4:3</span><span class="sxs-lookup"><span data-stu-id="c3d94-140">4:3</span></span>  | <span data-ttu-id="c3d94-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="c3d94-141">90x74.3</span></span> | <span data-ttu-id="c3d94-142">Frequenza dei fotogrammi massimo 15.</span><span class="sxs-lookup"><span data-stu-id="c3d94-142">Max framerate 15.</span></span>

<span data-ttu-id="c3d94-143">E ovviamente il `camera_fps` anche.</span><span class="sxs-lookup"><span data-stu-id="c3d94-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="c3d94-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="c3d94-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="c3d94-145">Recupero di un Frame di colore</span><span class="sxs-lookup"><span data-stu-id="c3d94-145">Getting a Color Frame</span></span>

<span data-ttu-id="c3d94-146">Recupero dei dati per un intervallo di colori e un frame di profondità è una procedura molto simile.</span><span class="sxs-lookup"><span data-stu-id="c3d94-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="c3d94-147">Prima di tutto è ottenere un'acquisizione dal dispositivo, quindi vengono estratte le immagini a colori da quest'ultimo e quindi è estrarre i dati non elaborati da tale immagine.</span><span class="sxs-lookup"><span data-stu-id="c3d94-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

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

<span data-ttu-id="c3d94-148">I dati archiviati in `colorDataBRGA` dipende dal formato è indicati nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="c3d94-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="c3d94-149">Poiché si è richiesto `K4A_IMAGE_FORMAT_COLOR_BGRA32`, abbiamo una matrice di valori di colori a 32 bit archiviati in BGRA order!</span><span class="sxs-lookup"><span data-stu-id="c3d94-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="c3d94-150">In questo caso, i file TGA archiviano colori nell'ordine BGR già!</span><span class="sxs-lookup"><span data-stu-id="c3d94-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="c3d94-151">E poiché la funzione di salvataggio è possibile ignorare il canale alfa con questi argomenti, è possibile passare solo i dati dell'immagine è!</span><span class="sxs-lookup"><span data-stu-id="c3d94-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="c3d94-152">Pulizia</span><span class="sxs-lookup"><span data-stu-id="c3d94-152">Cleaning Up</span></span>

<span data-ttu-id="c3d94-153">E come sempre, ricordarsi di rilasciare le risorse al termine con loro!</span><span class="sxs-lookup"><span data-stu-id="c3d94-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="c3d94-154">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="c3d94-154">Full Source</span></span>

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="c3d94-155">Laboratorio successivo - [combinazione colori e i dati di profondità](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="c3d94-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>