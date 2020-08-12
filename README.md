# Skin Hearing PCB Repository

Altium files Repository for Skin Hearing project. The Main Board houses the microcontroller and options for audio inputs. The Flex Electrodes is a two-way configurable flex PCB for skin stimulating electrodes.

<img src ="/assets/Skinhearing_proto_1.jpg" width="400">

<img src ="/assets/Skinhearing_proto_2.jpg" width="400">

## Features
Main board: 4 Layers
* STM32F410 microcontroller
* 1x CP2104 USB-UART bridge
* 1x SPH0645LM4H-B Digital microphone
* 1x SPV1840LR5H-B Analog microphone
* 1x MAX9814 Audio amplifier
* 1x 3.5mm audio jack for external microphone
* 2x LED7708 LED drivers to control electrode current
* 1x 32pin FCC connector for electrodes
* 1x Button
* 1S Battery charger and LDO

Flex Electrodes:
* Configuration 1: solder 0Ω resistors on R3 and R2, leave R1 and R4 not populated
* Configuration 2: solder 0Ω resistors on R1 and R4, leave R2 and R3 not populated

## Connections and Pinout
STM32F410:

|Signal|Pin|Notes|
|:---:|:----:|:---:|
|USART1_TX|PA9|Programming|
|USART1_RX|PA10|Programming|
|Button|PA0||
|MIC_AMP|PB0|output of audio amplifier|
|I2S1_WS|PA4|digital mic|
|I2S1_CK|PA5|digital mic|
|I2S1_SD|PA7|digital mic|
|LE|PB12|LED driver|
|DCLK|PB13|LED driver|
|DOUT|PB14|LED driver|
|DIN|PB15|LED driver|
|GSSY|PA8|LED driver|
|XFLT|PA11|LED driver|
|IOK|PB5|LED driver|
|XVOK|PB6|LED driver|
|XOVF|PB7|LED driver|
|XMSK|PB8|LED driver|


## Programming instructions

1. Download and install [CP210x drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
2. 	Make sure the BOOT config resitors are soldered properly to program over UART
BOOT0= HIGH, BOOT1=LOW
    * R18 and R23 soldered
    * R19 and R21 not populated
3. Get [STM32 flasher](https://www.st.com/en/development-tools/flasher-stm32.html) from the ST Website
4. Make sure your USB cable has communication wires!

## Firmware
Did not get consent to share

## Errata, fixes and debugging notes

#### Changes from rev 1.0
*	Removed R7 and R8 to improve USB reliability
* Corrected TX/RX connection on the CP2104 Chip
* Added Ground connections to the FPC connector
* Renamed channels to match the electrodes Flex PCB

#### Manufacturing notes
* Main board: 4L, 1.6mm thickness, 30x30mm

<img src ="/assets/Skinhearing_altium_3.png" width="300">


* Electrodes: FPC. See layer stack-up below

<img src ="/assets/layerStack.png" width="300">
<img src ="/assets/To FPC connector.png" width="300">

#### Suggestions for future designs
*	Industrial design considerations: position of buttons, LED and connectors
* In case LED drivers produce discomfort: consider using a DAC and an improved Howland current pump to control the outputs to the electrodes.
* Remove redundant audio input source once you've tested all of them
* Consider communication with other devices: ex: Bluetooth

## Datasheets
* [LED7708](https://www.st.com/resource/en/datasheet/led7708.pdf)
* [MAX9814](https://datasheets.maximintegrated.com/en/ds/MAX9814.pdf)
* [STM32F410 - 48Pin](https://www.st.com/resource/en/datasheet/stm32f410cb.pdf)
* [SPV1840LR5H-B](https://www.knowles.com/docs/default-source/model-downloads/spv1840lr5h-b-rev-b-datasheet.pdf)
* [SPH0645LM4H-B](https://cdn-shop.adafruit.com/product-files/3421/i2S+Datasheet.PDF)
* [CP2104](https://www.silabs.com/documents/public/data-sheets/cp2104.pdf)

## References and Tutorials
* Examples for LED7708 firmware : [evaluation boards](https://www.st.com/content/st_com/en/products/evaluation-tools/solution-evaluation-tools/led-and-general-lighting-solution-eval-boards/steval-ill035v1.html#resource) and [software](https://www.st.com/content/st_com/en/products/evaluation-tools/solution-evaluation-tools/led-and-general-lighting-solution-eval-boards/steval-ill035v1.html#tools-software)
* [STM32F4 tutorials](http://stm32f4-discovery.net)
