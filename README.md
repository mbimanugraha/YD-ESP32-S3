# YD-ESP32-S3 Core Board 

###### 简介：
The YD-ESP32-S3 core board is designed by VCC-GND Studio. If you need it, you can visit www.vcc-gnd.com to purchase it. The device uses the ESP32-S3 chip and can be used as a test prototype for IoT applications and can also be used for practical applications. It is equipped with two USB ports, one is a hardware USB to serial port (CH343P WCH Qinheng), and the other is the USB port of ESP32-S3.

![](/IMG/img1.PNG)

This guide will help you quickly get started with YD-ESP32-S3 and provide detailed information about the development board.

YD-ESP32-S3 is an entry-level development board equipped with Wi-Fi + Bluetooth® LE module ESP32-S3-WROOM-1.

Most of the pins of the modules on the board have been brought out to the pin headers on both sides of the development board. Developers can easily connect a variety of peripheral devices through jumpers according to actual needs, or plug the development board into a breadboard for use.

![img](/IMG/YD-ESP32-S3.PNG)

1. This is the smallest core board of ESP32-S3, using the ESP32-S3 module of Espressif.
2. The LDO circuit is dedicated to the wireless function, so there is no need to worry about insufficient current (power).
3. It is equipped with a WS2812-RGB LED (note that it is not directly lit through GPIO).
4. The RST button is used for external reset function and boot button (with the RST button, it can be used as a user button after reset, which is GPIO0).
5. You will find that the board has two TYPE-C interfaces (one is directly connected to USB (GPIO19 GPIO20), and the other is a USB to serial port USB port), equipped with a hardware USB to serial port chip (CH343).

###### Hardware Introduction:

![](/IMG/img2.png)

| Main Components                                 | Information                                                         |
| :--------------------------------------- | ------------------------------------------------------------ |
| ESP32-S3-WROOM-1 | ESP32-S3-WROOM-1 is a general-purpose Wi-Fi + Bluetooth low energy MCU module with rich peripheral interfaces, powerful neural network computing power and signal processing capabilities, designed for the artificial intelligence and AIoT markets. ESP32-S3-WROOM-1 uses a PCB onboard antenna. |
| 5 V to 3.3 V LDO | Power converter, input 5 V, output 3.3 V, current is 1A |
| Pin Headers | All available GPIO pins (except the flash SPI bus) are led out to the pin headers of the development board.  |
| USB-to-UART Port | Type-c-USB port, which can be used as the power supply port of the development board, can be used to burn firmware to the chip, and can also be used as a communication port to communicate with the chip through the onboard USB to UART bridge. |
| Boot Button | Download button. Press the **Boot** key and the **Reset** key to enter the "Firmware Download" mode and download the firmware through the serial port. If the boot is complete, it can be used as a normal input key, and the IO used is GPIO0. |
| Reset Button | Reset button. |
| USB Port | ESP32-S3 USB OTG port, supporting full-speed USB 1.1 standard. The ESP32-S3 USB port can be used as the power supply port of the development board, can be used to burn firmware to the chip, can communicate with the chip through the USB protocol, and can also be used for JTAG debugging.  |
| USB-to-UART Bridge | The chip is CH343P, the manufacturer is Qinheng, the website is http://www.wch-ic.com/ Driver: http://www.wch-ic.com/products/CH343.html? |
| RGB LED | Addressable RGB light-emitting diode, driven by GPIO48. Model is WS2812. |
| PWR LED | Power indicator light, lights up after the board is powered, and cannot be controlled by the program. |
| TX LED | The led on the serial port TXD line of ESP32-S3, when serial port data is sent, the LED flashes, if the serial port function is not used, it can be used as GPIO, GPIO43 |
| RX LED | The led on the serial port RXD line of ESP32-S3, when serial port data is received, the LED flashes, if the serial port function is not used, it can be used as GPIO, GPIO44 |


###### Remark:

On development boards with the ESP32-S3-WROOM-1 module series (using 8-wire SPI flash/PSRAM), pins GPIO35, GPIO36, and GPIO37 are used for communication between the internal ESP32-S3 chip and the SPI flash/PSRAM and are not available externally.



###### Start developing your application:
Before powering on, make sure the development board is in good condition.



###### Functional block diagram:
The main components and connections of YD-ESP32-S3 are shown in the figure below:

![](/IMG/img4.png)



###### Power Options:
You can choose to power the board from one of the following three power supply methods:

USB to UART interface power supply or ESP32-S3 USB interface power supply (choose one or both), default power supply method (recommended)

5V and G (GND) pin header power supply

3V3 and G (GND) pin header power supply

###### Pin headers:
The following table lists the names and functions of the pin headers (P1 and P2) on both sides of the board. The names of the pin headers are shown in the front of the YD-ESP32-S3 figure, and the pin numbering is consistent with the board schematic (PDF).

###### P1

| Pin Number | Pin Name | Type  | Information                                                         |
| ---- | ---- | ----- | ------------------------------------------------------------ |
| 1    | 3V3  | P     | 3.3 V 电源                                                   |
| 2    | 3V3  | P     | 3.3 V 电源                                                   |
| 3    | RST  | I     | EN                                                           |
| 4    | 4    | I/O/T | RTC_GPIO4, GPIO4, TOUCH4, ADC1_CH3                           |
| 5    | 5    | I/O/T | RTC_GPIO5, GPIO5, TOUCH5, ADC1_CH4                           |
| 6    | 6    | I/O/T | RTC_GPIO6, GPIO6, TOUCH6, ADC1_CH5                           |
| 7    | 7    | I/O/T | RTC_GPIO7, GPIO7, TOUCH7, ADC1_CH6                           |
| 8    | 15   | I/O/T | RTC_GPIO15, GPIO15, U0RTS, ADC2_CH4, XTAL_32K_P              |
| 9    | 16   | I/O/T | RTC_GPIO16, GPIO16, U0CTS, ADC2_CH5, XTAL_32K_N              |
| 10   | 17   | I/O/T | RTC_GPIO17, GPIO17, U1TXD, ADC2_CH6                          |
| 11   | 18   | I/O/T | RTC_GPIO18, GPIO18, U1RXD, ADC2_CH7, CLK_OUT3                |
| 12   | 8    | I/O/T | RTC_GPIO8, GPIO8, TOUCH8, ADC1_CH7, SUBSPICS1                |
| 13   | 3    | I/O/T | RTC_GPIO3, GPIO3, TOUCH3, ADC1_CH2                           |
| 14   | 46   | I/O/T | GPIO46                                                       |
| 15   | 9    | I/O/T | RTC_GPIO9, GPIO9, TOUCH9, ADC1_CH8, FSPIHD, SUBSPIHD         |
| 16   | 10   | I/O/T | RTC_GPIO10, GPIO10, TOUCH10, ADC1_CH9, FSPICS0, FSPIIO4, SUBSPICS0 |
| 17   | 11   | I/O/T | RTC_GPIO11, GPIO11, TOUCH11, ADC2_CH0, FSPID, FSPIIO5, SUBSPID |
| 18   | 12   | I/O/T | RTC_GPIO12, GPIO12, TOUCH12, ADC2_CH1, FSPICLK, FSPIIO6, SUBSPICLK |
| 19   | 13   | I/O/T | RTC_GPIO13, GPIO13, TOUCH13, ADC2_CH2, FSPIQ, FSPIIO7, SUBSPIQ |
| 20   | 14   | I/O/T | RTC_GPIO14, GPIO14, TOUCH14, ADC2_CH3, FSPIWP, FSPIDQS, SUBSPIWP |
| 21   | 5V   | P     | 5 V 电源                                                     |
| 22   | G    | G     | 接地                                                         |

###### P2

| Pin Number | Pin Name | Type | Information                                                 |
| ---- | ---- | ----- | ----------------------------------------------------- |
| 1    | G    | G     | 接地                                                  |
| 2    | TX   | I/O/T | U0TXD, GPIO43, CLK_OUT1                               |
| 3    | RX   | I/O/T | U0RXD, GPIO44, CLK_OUT2                               |
| 4    | 1    | I/O/T | RTC_GPIO1, GPIO1, TOUCH1, ADC1_CH0                    |
| 5    | 2    | I/O/T | RTC_GPIO2, GPIO2, TOUCH2, ADC1_CH1                    |
| 6    | 42   | I/O/T | MTMS, GPIO42                                          |
| 7    | 41   | I/O/T | MTDI, GPIO41, CLK_OUT1                                |
| 8    | 40   | I/O/T | MTDO, GPIO40, CLK_OUT2                                |
| 9    | 39   | I/O/T | MTCK, GPIO39, CLK_OUT3, SUBSPICS1                     |
| 10   | 38   | I/O/T | GPIO38, FSPIWP, SUBSPIWP                              |
| 11   | 37   | I/O/T | SPIDQS, GPIO37, FSPIQ, SUBSPIQ                        |
| 12   | 36   | I/O/T | SPIIO7, GPIO36, FSPICLK, SUBSPICLK                    |
| 13   | 35   | I/O/T | SPIIO6, GPIO35, FSPID, SUBSPID                        |
| 14   | 0    | I/O/T | RTC_GPIO0, GPIO0                                      |
| 15   | 45   | I/O/T | GPIO45                                                |
| 16   | 48   | I/O/T | GPIO48, SPICLK_N, SUBSPICLK_N_DIFF, RGB LED           |
| 17   | 47   | I/O/T | GPIO47, SPICLK_P, SUBSPICLK_P_DIFF                    |
| 18   | 21   | I/O/T | RTC_GPIO21, GPIO21                                    |
| 19   | 20   | I/O/T | RTC_GPIO20, GPIO20, U1CTS, ADC2_CH9, CLK_OUT1, USB_D+ |
| 20   | 19   | I/O/T | RTC_GPIO19, GPIO19, U1RTS, ADC2_CH8, CLK_OUT2, USB_D- |
| 21   | G    | G     | 接地                                                  |
| 22   | G    | G     | 接地                                                  |

P: power supply; I: input; O: output; T: can be set to high impedance.

###### Pin Diagram:

![](/IMG/img11.jpg)

###### Official link of CH340 chip driver:

http://www.wch-ic.com/products/CH340.html?        ENGLISH

https://www.wch.cn/products/CH340.html?from=list     中文

Micropython Firmware Download:

ESP32-S3 download erase tool software flash_download_tool_3.9.2_0 in Windows download tool.
Note: No need to install and unzip, double-click the small gear icon, select ESP32-S3, develop, USART, and look at the picture. Note that the starting address is 0x00, check the front. If you can't download, it may be that the USB to serial port driver is not installed. Solve the driver problem first and then download.

![](/IMG/img3.png)
Note:

You cannot use the so-called ESP32 downloader provided by thonny to download micropython firmware for ESP32-S3 (the one provided by thonny is for esp32 download, the model is not esp32-s3 and the address is not 0x00 of S3 but 0x1000 of ESP32), nor can you use the firmware with SPRAM officially downloaded by micropython, which cannot be used normally after downloading. The correct download method is to use the official flash tool download tool of Espressif, select ESP32-S3 serial port download (USART), insert the USB of the COM port of the board, select the corresponding firmware (the firmware adapted by our source), the starting address is 0x00, check the firmware before selecting it, it is best to erase it before downloading.
The firmware is linked at the beginning of 1- and the firmware download software is linked at the beginning of 2-. Please note that it is best to update the hardware driver of CH343usb to serial port before use. The precautions are in the data link at the beginning of 0-. Confirm that there is the word COM of CH343 in the device manager.

 If you want to download TASMOTA firmware, TASMOTA has its own official web download.

https://tasmota.github.io/docs/

If you download your own firmware file, you can use Espressif's download tool.

https://www.espressif.com.cn/en/home

This text is the information of ESP32-S3.  Basic information includes (hardware serial port CH343 driver, source version micropython firmware, software for downloading firmware, micropython IDE, schematic diagram, etc.): http://124.222.62.86/yd-data/YD-ESP32-S3/ 

If you plan to use the official idf-C language programming detailed information link (the routine is the API reference): https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32s3/get-started/index.html 

If you plan to use Ardiuno programming information link: https://docs.espressif.com/projects/arduino-esp32/en/latest/getting_started.html#about-arduino-esp32 

If you plan to use micropython language programming information link as follows (note that the quick start is to see ESP32):  https://docs.micropython.org/en/latest/esp32/quickref.html
###### Problems with copycat/fake/poor-quality imitations:

There are many copycat/fake/poor-quality imitations of our source (YD) development boards, and the most rampant one is Shenzhen Huaqiangbei. The usual form of copycats is to directly polish our development boards and take photos to copy the boards, resulting in many hidden dangers in copycat products. Now we summarize the hazards (hidden dangers) of buying copycat boards.
 Take the YD-ESP32 (ESP32/S2/S3/C3) series as an example:

1. In order to further pursue profits, copycat manufacturers often use refurbished, unofficial devices, arbitrarily replace them with cheap models with the same package, randomly select models, and seek profits

2. The 2812 light does not weld signals, and 2812 cannot be used. This indirectly proves that the plagiarist does not check the board, saves trouble, and reduces costs

3. The copycat board is not inspected before leaving the factory (cost reduction), and it is packaged and sent to consumers after the production line, saving links and seeking profits

4. The copycat board is copied from photos, and many silk screens are copied incorrectly, which is easy to mislead consumers, and the plagiarists themselves can't figure it out

5. The copycat board is copied from version 1.2, which is an early version in 2022. The genuine version is version 1.4. The copycat cannot use the updated functions, and it saves trouble without improvement

6. The copycat board uses a third-party "copycat" module (low cost). The copycat module has not been impedance matched and is not used when using WIFI  When using Bluetooth, the power consumption is high, the signal is poor, and the system crashes easily.

7. Since the copycat board cannot find our dedicated LDO on the market, it arbitrarily chooses inappropriate models, such as 1117 (low cost), with large voltage difference, easy to crash, and poor signal.

8. The copycat board uses a high-voltage difference diode (greater than 0.7V tube voltage drop, low cost), which causes insufficient voltage difference of the back-end LDO, further causing high power consumption, easy to crash, and poor signal.

9. The copycat board does not provide basic technology, and even the information is directly copied from us (the information is still our early information, and the copycats are too lazy to find the latest information). After receiving the money, they don’t care.

10. Sometimes there is a problem when the copycat board starts, and it directly enters the BootLoader, causing it to be unusable. The copycats don’t understand what the problem is!

11. Since the copycat board counterfeiters copy the board from photos, there is no schematic diagram, which makes users unable to understand how to use it, and the copycats don’t understand it either, making the product difficult to use.

 Some counterfeiters directly print words such as YD-ESP32 on the counterfeit boards to confuse the public. What's worse, some even print our official website WWW.VCC-GND.COM on the counterfeit products. This behavior has triggered relevant laws and we will definitely investigate. Consumers are requested not to take the above risks for the sake of a few cents or a few dollars of temporary cheapness, wasting time and energy in vain. Support the source and support the genuine products. Please identify the source and VCC-GND trademark when purchasing.

###### Any function on the pin can be realized through the internal switching matrix:

In the introduction of various ESP32 series documents, it is noted that it has various peripheral communication functions such as I2C, I2S, UART, SPI, etc. However, the schematic diagram on the functional pins does not indicate which pins these functions are.  This question is answered in the peripheral pin allocation. Peripheral interfaces such as I2C, I2S, UART, SPI, etc. can be defined as any GPIO pin, so there is no need to mark them on the functional diagram. Anyway, any GPIO can be assigned a pin function required by the I2C, I2S, UART, SPI functions of these peripheral interfaces.



