## Raspberry Pi CM4 Carrier Board for LEGO SPIKE Prime

This is the final project for my Microcontrollers Programming Class. My professor gave us an open prompt which is "create something that is useful". With my previous experience and interests in designing LEGO Robotics expansion hardware, I developed a Raspberry Pi CM4 Carrier board specifically for the LEGO SPIKE Prime educational system. In short, this is a slim, self-contained add-on to the SPIKE Prime hub. It gives the educational platform a huge boost in computational power and peripheral connectivity, making it capable of running tasks such as image processing, machine learning, ROS, and more.

**Note: As of June 23rd, 2021, the camera ports unfortunately do not work on the current version (in short, I made a dumb mistake of using a different footprint for the camera connectors, which has all the pins backwards). Connecting a camera may result in the flex cable heating up or possibly some permanent damage to the CM$ board. If I ever got the chance to make another design iteration, this will be the first thing I will tackle.**

Youtube: https://youtu.be/AbPgGo25kjA

GrabCAD: https://grabcad.com/library/raspberry-pi-cm4-carrier-board-for-lego-spike-prime-1

For more information about this project, please checkout https://www.yufengwu.com/work/class-projects/cm4-carrier-board

![Rendering](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/Render-with-case.JPG)
![Finished](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/IMG_4302.JPEG)

## Hardware Components
To make this backpack yourself, you'll need the following hardware components:
* The carrier board PCB itself. I got the full assembly service from PCBWay, but you are welcome to find your own PCB manufacturer.
* A [Raspberry Pi Compute Module 4](https://www.raspberrypi.org/products/compute-module-4/?variant=raspberry-pi-cm4001000) **with onboard EMMC and WiFi module**. 
* Some right-angle pin headers. [Amazon Link](https://www.amazon.com/Uxcell-a14032500ux0426-Right-Header-Spacing/dp/B010ESD338/ref=sr_1_3?dchild=1&keywords=right+angle+pin+headers&qid=1624248428&sr=8-3)
* A 3.7V Lithium Polymer (LiPoly) battery with JST-PH connector in the correct polarity. It has to be both slim enough to fit inside the housing and powerful enough to handle around 1.5A nominal and 3A burst current. [Digikey Link](https://www.digikey.com/en/products/detail/jauch-quartz/LP605060JU-PCM-WIRES-70MM/9560993?s=N4IgTCBcDaIDYAcBsAGArC1ArAriAugL5A)
* A short microB male to microB male USB cable. [Digikey Link](https://www.digikey.com/en/products/detail/CAB0701/1778-1018-ND/6928231?itemSeq=364421679)
* A standard hobbyist 3D printer with PLA filament (Prusa MK3S, Prusa MINI, Ender3, etc.).


## Getting Started with the Carrier Board
1. Install the compute module onto the carrier board. Make sure to get one with EMMC memory (you probably want one with WiFi as well)
![CM4](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/1.jpeg)

1. Close the jumper (see pic) to disable EMMC boot. 
![Jumper Open](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/2.jpeg)
![Jumper Closed](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/3.jpeg)

1. Connect a microUSB data cable from the OTG port (the one closer to the corner) to your laptop.
![OTG](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/4.jpeg)

1. Follow [this link](https://www.raspberrypi.org/documentation/hardware/computemodule/cm-emmc-flashing.md) to flash the compute module's EMMC. The spscific steps depend on your computer's operating system (see the link for details). After this, you should have an operating system of your choice installed on the compute module. 

1. To minimize its size, this board is designed to have your Pi communicate with your computer via a serial console cable. You may now follow [this link](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/overview) to set up the communication. As for the "Connecting the Lead" section, refer to the following picture for wiring. Specifically, you'll want the following line of text be added to the last line of config.txt, which you may found in your Pi as a mass storage device right after writing the OS onto your compute module.
    ```
    enable_uart=1
    ```
![Serial Console](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/6.jpeg)

1. For thir carrier board specifically, you also might want to add the following to config.txt, since the GPIO pins for UART5 were also made available in case you want to use the console cable and UART at the same time.
    ```
    dtoverlay=uart5
    ```

1. If the TTL cable connection is successful, you may continue to set up other hardware, such as WiFi and USB, in order to release the full potential of your compute module. You may use a short microB male to microB male USB cable to connect your carriar board to a LEGO SPIKE Prime. To enable USB, add the following line to config.txt:
    ```
    dtoverlay=dwc2,dr_mode=host
    ```

1. Happy hacking!



