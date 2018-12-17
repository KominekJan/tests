## Windows:
* install Python3 
* download MicroPython [1] https://micropython.org/download#esp32
* install esptool.py [2] https://github.com/espressif/esptool
* install ampy [3] https://github.com/adafruit/ampy 
<pre>
set AMPY_PORT=COM6
ampy ls
AMPY_BAUD=115200
</pre>
* connect ESP32 and detect COM port
* erase FLASH: 
    During this phase the BOOT button needs to be pressed down until connection is established.
    <pre>esptool.py --chip esp32 -p /COM6 erase_flash</pre>
* upload Micropython bin: 
    <pre>esptool.py --chip esp32 -p /COM6 write_flash -z 0x1000 ./down/esp32-20180821-v1.9.4-479-g828f771e3.bin</pre>

</pre>