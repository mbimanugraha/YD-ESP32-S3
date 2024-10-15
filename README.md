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

###### 硬件介绍：

![](/IMG/img2.png)

| 主要组件                                 | 介绍                                                         |
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


###### 备注:

在板载 ESP32-S3-WROOM-1 模组系列（使用 8 线 SPI flash/PSRAM）的开发板，管脚 GPIO35、GPIO36 和 GPIO37 已用于内部 ESP32-S3 芯片与 SPI flash/PSRAM 之间的通信，外部不可使用。



###### 开始开发应用:
通电前，请确保开发板完好无损。



###### 功能框图：
YD-ESP32-S3 的主要组件和连接方式如下图所示：

![](/IMG/img4.png)



###### 电源选项:
您可从以下三种供电方式中任选其一给开发板供电：

USB 转 UART 接口供电或 ESP32-S3 USB 接口供电（选择其一或同时供电），默认供电方式（推荐）

5V 和 G (GND) 排针供电

3V3 和 G (GND) 排针供电

###### 排针:
下表列出了开发板两侧排针（P1 和 P2）的 名称 和 功能，排针的名称如图 YD-ESP32-S3正面 所示，排针的序号与 开发板原理图 (PDF) 一致。

###### P1

| 序号 | 名称 | 类型  | 功能                                                         |
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

| 序号 | 名称 | 类型  | 功能                                                  |
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

P：电源；I：输入；O：输出；T：可设置为高阻。

###### 引脚图：

![](/IMG/img11.jpg)

###### CH340芯片的驱动官方链接：

http://www.wch-ic.com/products/CH340.html?        ENGLISH

https://www.wch.cn/products/CH340.html?from=list     中文

Micropython固件下载：

ESP32-S3的下载擦除工具软件flash_download_tool_3.9.2_0在win下downloard tool。
注意：无需安装解压既用，双击小齿轮标志，选择ESP32-S3，develop，USART，剩下看图片，注意起始地址为0x00，前面打对号。如果不能下载可能是USB转串口驱动没有安好，先处理好驱动问题再来下载。

![](/IMG/img3.png)

注意：

不能用thonny自带的所谓的ESP32下载器给ESP32-S3下载micropython固件(thonny自带的是给esp32下载的，型号并不是esp32-s3  地址也并不是S3的0x00而是ESP32的0x1000)，也不能使用micropython官方下载的带SPRAM固件，下载后也不能正常使用，正确的下载方式是使用乐鑫官方的flash tool下载工具，选择ESP32-S3 串口下载（USART）插入板子的COM端口的usb，选择对应的固件（我们源地自己改编的固件）起始地址是0x00 固件选择前打对号，最好先擦除再下载。
固件是1-开头链接的和固件下载软件是2-开头的链接，注意使用前最好更新一下CH343usb转串口的硬件驱动，注意事项在0-开头的资料链接中，在设备管理器中确认出现有……CH343字样COM才行。

如果下载TASMOTA固件，TASMOTA官方有自己的web下载。

https://tasmota.github.io/docs/

如果你下载自己的固件文件可以使用乐鑫的下载工具。

https://www.espressif.com.cn/en/home

这段文字是ESP32-S3的资料。 基础资料包括（硬件串口CH343驱动，源地版本micropython固件，下载固件的软件、micropython的IDE、原理图尺寸图等）：http://124.222.62.86/yd-data/YD-ESP32-S3/ 

如果计划使用官方的idf-C语言编程详细资料链接（例程就是的API参考）： https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32s3/get-started/index.html 

如果计划使用Ardiuno编程资料链接： https://docs.espressif.com/projects/arduino-esp32/en/latest/getting_started.html#about-arduino-esp32 

如果计划使用micropython语言编程资料链接如下（注意快速入门看ESP32就行）： https://docs.micropython.org/en/latest/esp32/quickref.html
###### 山寨/假冒/劣质仿造的问题：

寨/假冒/劣质仿造我们源地（YD）开发板有很多，以深圳华强北最为猖獗，山寨者惯用的形式为直接打磨我们的开发板进行拍照抄板，以致山寨的产品隐患重重。现总结购买山寨板的危害（隐患）。
以YD-ESP32（ESP32/S2/S3/C3）系列为例：

1、山寨厂家为进一步追求利润，往往使用翻新，非官方器件，任意替换为同封装的廉价型号，乱选型，图利润

2、2812灯不焊接信号，无法使用2812，从侧面印证抄袭者不检查板子，图省事，压成本

3、山寨板出厂不检查（压缩成本），下完生产线就包装，发给消费者，省环节，图利润

4、山寨板由于照片抄袭，多处丝印抄错，容易误导消费者，抄袭者自己都搞不明白

5、山寨板抄袭是1.2版本是2022年早期版本，正版是1.4版本，山寨无法使用更新的功能，图省事不改进

6、山寨板使用的是第三方“山寨”模组（成本低），山寨模组没有经过阻抗匹配，在使用WIFI 蓝牙时候，功耗高信号差、易死机

7、山寨板由于在市面上找不到我们用专用LDO，就任意选择不合适型号，例如1117（成本低），压差大，易死机，信号差

8、山寨板使用高压差的二极管（大于0.7V管压降，成本低），造成后端LDO压差不足，进一步造成功耗高，易死机，信号差

9、山寨板不提供基本技术，就连资料都是直接复制我们的（资料还是我们早期的，最新资料山寨者都懒得找），钱收后，就不管了

10、山寨板启动有时候有问题，直接进入BootLoader，造成无法使用，山寨者都不明白这是什么问题！

11、山寨板仿冒者由于是照片抄板，所以没有原理图，让用户搞不懂如何使用，山寨者也不懂，造成产品难以使用。


有山寨者直接在山寨板子上印有YD-ESP32等字样以此来混淆视听，更有甚者，将我们官方网址WWW.VCC-GND.COM印在山寨仿冒品上，该行为已经触发相关法律，我们定会追究，请广大消费者不要贪图几毛钱~几块的一时便宜而承担以上种种风险，白白浪费时间和精力，支持源地支持正品，购买请认准源地，VCC-GND商标。

###### 通过内部交换矩阵可以实现引脚上的任意功能：

在各种ESP32系列文档介绍中注明了具备各种外设通讯功能例如I2C、I2S、UART、SPI等。但是又在功能引脚上示意图没有标注这些功能是哪个引脚。这个疑问在外设管脚分配中得到了解答，诸如I2C、I2S、UART、SPI等外设接口可以被定义为任意GPIO管脚，所以就没有必要在 功能示意图上标注出来了，反正任何一个GPIO都可以赋予这些外设接口I2C、I2S、UART、SPI功能所需要的引脚某个引脚功能。



