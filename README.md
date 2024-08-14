# AP33772_web_browser_control
AP33772 (USB PD controller) controlled by a web browser. An ESP32C3 board with MicroPython script allows for wireless control of a USB PD wall adapter.


This project uses 3 separate board connected together on a small proto board. The first board is the Mikroe USB-C Sink 2 Click, which I used to develop my AP33772_I2C MicroPython driver (also used in this project).
The second board is the Seeed Xiao ESP32C3 with the latest MicroPython installed. The AP33772.py file needs to be downloaded to the flash memory and the included esp32c3_web_ap33772_control.py script should be saved as "main.py" in the flash memory.
The last board is a 3 pin LDO board which takes the VBUS voltage and outputs a regulated 3.3V for the Xiao ESP32C3 board. I buy these boards in 10 packs on Amazon (https://www.amazon.com/dp/B01HXU1NQY) and then remove the LDO package and replace it with an LDO that can work with voltages up to 20V, NCV1117ST33T3G from ONSEMI (https://www.digikey.com/en/products/detail/onsemi/NCV1117ST33T3G/1483937?so=88002084). I modify the Mikroe board to take the VBUS voltage and connect it to an unsed pin. The VBUS pin becomes the input voltage for the LDO board and the 3.3V output connects to the Xiao's 3.3V pin (ground connection shared with all 3 boards). All boards are powered by a USB C wall adapter connected to the Mikroe board by a type C cable. The Mikroe board orange power terminal will initially have 0V, but the wall adapter is providing 5V.

