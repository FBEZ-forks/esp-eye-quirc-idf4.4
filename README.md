# Qrcode reading with Quirc example

In this examples, after a booting log, the example emits the qr-code read.
It uses the [quirc](https://github.com/dlbeer/quirc) libray [idf extra component](https://github.com/espressif/idf-extra-components/tree/master/quirc).

This example has been tested on an ESP-EYE with `OV3660` camera.

This repo is to show where the esp32-camera components stops to work as expected.

## Tested ESP32-Camera commits

The qr-code used to test the code is represented below.
![tested qr code](extra/tested_qr_code.png)

* `86a4951`: working  

### Working log (86a4951)
```
I (875) app_peripherals: Camera module is ESP-EYE
I (875) gpio: GPIO[5]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:2 
I (885) cam_hal: cam init ok
I (895) sccb: pin_sda 18 pin_scl 23
I (905) camera: Detected camera at address=0x3c
I (905) camera: Detected OV3660 camera
I (905) camera: Camera PID=0x3660 VER=0x00 MIDL=0x00 MIDH=0x00
I (1225) esp32 ll_cam: node_size: 3840, nodes_per_line: 1, lines_per_node: 4, dma_half_buffer_min:  3840, dma_half_buffer: 15360, lines_per_half_buffer: 16, dma_buffer_size: 30720, image_size: 57600
I (1225) cam_hal: buffer_size: 30720, half_buffer_size: 15360, node_buffer_size: 3840, node_cnt: 8, total_cnt: 3
I (1235) cam_hal: Allocating 57600 Byte frame buffer in PSRAM
I (1245) cam_hal: Allocating 57600 Byte frame buffer in PSRAM
I (1255) cam_hal: cam config ok
I (1265) ov3660: Calculated VCO: 160000000 Hz, PLLCLK: 160000000 Hz, SYSCLK: 40000000 Hz, PCLK: 10000000 Hz
0/1]Data: This is a test for esp32-camera
0/1] DECODE FAILED: Format data ECC failure
0/1]Data: This is a test for esp32-camera
0/1]Data: This is a test for esp32-camera
```

## Notes

Please note that there is a minimum distance at which the camera can focus on the qr code. This also put a limit to the minimum side of the qr code. If the qr code is nearer than 5 to 6 cm, it may be necessary to put an additional lens (crf. reference nr. 1).

In the table below are recorded a few couples of lens distance and qr-code side size.  

| Qr-code side length (cm) | Approx. Lens distance (cm) |
|---|---|
|6.5 | 17 |
|4 | 3| 
|2.5|6|


## References

+ [Minimum lens distance thread](https://electronics.stackexchange.com/questions/458332/shortest-focus-distance-of-ov2640-camera-modules-with-fixed-focus)
+ [Original esp-who example](https://github.com/espressif/esp-who/tree/master/examples/code_recognition)
