# What is it?

This is an ESP32-C3-MINI-1-N4 with RS485 and color touch TFT all together on one board. The ESP32-C3-MINI-1-N4 contains the ESP32-C3 SoC which is a successor for the well known ESP8266 microcontroller. The RS485 exists of auto-send-receive with MAX485 chip. And the touch screen is the ILI9341 screen with touch sensor.

IOT home users who want to talk to modbus devices generally some ready available components are connected together to create a arduino modbus capable device. However this is often not the best of connection due to all the wiring which is necessary between all the components. This board makes it easy and allows you to run you modbus code together with an easy visible color touch screen interface.

It is an intergrated complete design. Just connect power (USB-C) and your modbus device, upload some code, and you have a nice working device! The LCD connections to the GPIO's of the ESP32-C3-MINI-1-N4 is shown in one of the photo's. The RS485 is connected to the hardware uart rx/tx (gpio20/gpio21). Therefore you can't use serial output and RS485 together. But hey, just print your debugging info on the TFT screen!

The basic option contains of only the PCB with the ESP32-C3-MINI-1-N4, the USB-C connector and a soldered connector for the RS485 connection. This allows it to be used as basic ESP32-C3-MINI-1-N4 modbus master or slave. You can add the ILI9341 TFT screen with touchscreen to add the possibility to add custom design for your program to interact with the user. The 3d printed case is another option for complete PCB+TFT+case solution.

The module is powered using the USB-C connector or with external 5v soldered to the power connections on the board.

I am using this design for my Sofar inverter with the software Sofar2Mqtt for which I modified the code to work with this tft screen (see last two photos). This software will be pre-installed before shipping so I can test if everything is working correctly. You can overwrite it with your own program/code with any ESP32-C3 programmer if you don't want to use this software.

ESPhome can also be installed and it also provides support for the touchscreen (TFT screen and Touch sensor) but make sure to turn of logging via UART (set baudrate to 0) as the RS485 uses the onboard UART (tx/rx).

Make sure your code (Arduino, ESPHome) defines the GPIO pins correctly to connect to the TFT and touch sensor:

* Controller MOSI = GPIO7
* Controller MISO = GPIO2
* Controller SCLK = GPIO6
* TFT CS = GPIO1
* TFT DC = GPIO4
* TFT Reset = GPIO10
* TFT Backlight = GPIO5
* TOUCH CS = GPIO0
* TOUCH IRQ = GPIO3
