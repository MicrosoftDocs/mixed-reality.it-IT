# <a name="accessing-the-imu"></a><span data-ttu-id="fbec8-101">L'accesso al IMU</span><span class="sxs-lookup"><span data-stu-id="fbec8-101">Accessing the IMU</span></span>

<span data-ttu-id="fbec8-102">Azure Kinect DK contiene un'unità di misura inerziale (IMU).</span><span class="sxs-lookup"><span data-stu-id="fbec8-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="fbec8-103">Ciò può essere utile per aiutare a determinare lo spostamento e l'orientamento del dispositivo durante l'acquisizione.</span><span class="sxs-lookup"><span data-stu-id="fbec8-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="fbec8-104">In particolare se si dispositivo non è fisso.</span><span class="sxs-lookup"><span data-stu-id="fbec8-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="fbec8-105">**Contenuto:**</span><span class="sxs-lookup"><span data-stu-id="fbec8-105">**Contents:**</span></span>  
[<span data-ttu-id="fbec8-106">Installazione e configurazione</span><span class="sxs-lookup"><span data-stu-id="fbec8-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="fbec8-107">Recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="fbec8-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="fbec8-108">Pulizia</span><span class="sxs-lookup"><span data-stu-id="fbec8-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="fbec8-109">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="fbec8-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="fbec8-110">**Di seguito sono le funzioni che si userà:**</span><span class="sxs-lookup"><span data-stu-id="fbec8-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="fbec8-111">Installazione e configurazione</span><span class="sxs-lookup"><span data-stu-id="fbec8-111">Configuration and Setup</span></span>

<span data-ttu-id="fbec8-112">La configurazione qui è piuttosto semplice.</span><span class="sxs-lookup"><span data-stu-id="fbec8-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="fbec8-113">Nessun elemento è necessario specificare nella configurazione del dispositivo per IMU campionamento funzionare, ma si dovrà chiamare `k4a_device_start_cameras` prima corretto.</span><span class="sxs-lookup"><span data-stu-id="fbec8-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="fbec8-114">Al contrario, si verrà effettuata una chiamata a `k4a_device_start_imu` dopo avere avviato le fotocamere.</span><span class="sxs-lookup"><span data-stu-id="fbec8-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="fbec8-115">Recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="fbec8-115">Getting Data</span></span>

<span data-ttu-id="fbec8-116">![Immagine di app di esempio IMU](img/IMU.png "Ecco che cosa verrà compilata come esempio.")</span><span class="sxs-lookup"><span data-stu-id="fbec8-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="fbec8-117">Il IMU fornisce i dati con una frequenza di 1.6 kHz.</span><span class="sxs-lookup"><span data-stu-id="fbec8-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="fbec8-118">Che è una grande quantità di dati e questo significa che se si è interessati solo analizzarlo ogni volta che un frame di profondità/colore è disponibile, sarà possibile disporre di una coda di campioni IMU è in attesa.</span><span class="sxs-lookup"><span data-stu-id="fbec8-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="fbec8-119">Si noti che questi dati non sono un orientamento o posizione, ma piuttosto una misura della forza attualmente applicata al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fbec8-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="fbec8-120">È possibile agganciare un campione e rimuoverlo dalla coda chiamando `k4a_device_get_imu_sample` con un timeout di 0 millisecondi.</span><span class="sxs-lookup"><span data-stu-id="fbec8-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="fbec8-121">È necessario tornare `K4A_WAIT_RESULT_SUCCEEDED` purché disponga di esempio ed è disponibile!</span><span class="sxs-lookup"><span data-stu-id="fbec8-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="fbec8-122">Ecco un esempio di somma di tutti gli esempi attualmente nella coda e la stampa la Media.</span><span class="sxs-lookup"><span data-stu-id="fbec8-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="fbec8-123">Pulizia</span><span class="sxs-lookup"><span data-stu-id="fbec8-123">Cleaning Up</span></span>

<span data-ttu-id="fbec8-124">E come sempre, rilasciare tutti gli elementi quando hai finito :)</span><span class="sxs-lookup"><span data-stu-id="fbec8-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="fbec8-125">Codice sorgente completo</span><span class="sxs-lookup"><span data-stu-id="fbec8-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```