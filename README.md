## Raspberry Pi CM4 Carrier Board for LEGO SPIKE Prime

This is the final project for my Microcontrollers Programming Class. My professor gave us an open prompt which is "create something that is useful". With my previous experience and interests in designing LEGO Robotics expansion hardware, I developed a Raspberry Pi CM4 Carrier board specifically for the LEGO SPIKE Prime educational system. In short, this is a slim, self-contained add-on to the SPIKE Prime hub. It gives the educational platform a huge boost in computational power and peripheral connectivity, making it capable of running tasks such as image processing, machine learning, ROS, and more.

Youtube: https://youtu.be/AbPgGo25kjA

GrabCAD: https://grabcad.com/library/raspberry-pi-cm4-carrier-board-for-lego-spike-prime-1

For more information about this project, please checkout https://www.yufengwu.com/work/class-projects/cm4-carrier-board

![Rendering](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/Render-with-case.JPG)
![Finished](https://github.com/EricYufengWu/SPIKExCM4/blob/master/Documentation/IMG_4302.JPEG)


## Getting Started with the carrier board
1. Install the compute module onto the carrier board. Make sure to get one with EMMC memory (you probably want one with WiFi as well)
1. Close the jumper (see pic) to disable EMMC boot. 
1. Connect a microUSB data cable from the OTG port (the one closer to the corner) to your laptop.
1. Follow this link to flash the compute module's EMMC: https://www.raspberrypi.org/documentation/hardware/computemodule/cm-emmc-flashing.md. The spscific steps depend on your computer's operating system (see the link for details). After this, you should have an operating system of your choice installed on the compute module. 
1. To minimize its size, this board is designed to have your Pi communicate with your computer via a serial console cable. You may now follow this link to set up the communication: https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/overview. As for the "Connecting the Lead" section, refer to the following picture for wiring. Specifically, you'll want the following line of text be added to the last line of config.txt, which you may found in your Pi as a mass storage device right after writing the OS onto your compute module.
    ```
    enable_uart=1
    ```

1. For thir carrier board specifically, you also might want to add the following to config.txt, since the GPIO pins for UART5 were also made available in case you want to use the console cable and UART at the same time.
    ```
    dtoverlay=uart5
    ```

1. If the TTL cable connection is successful, you may continue to set up other hardware, such as WiFi and USB, in order to release the full potential of your compute module. You may use a short microUSB to microUSB cable to connect your carriar board to a LEGO SPIKE Prime. Have fun hacking!


