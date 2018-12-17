## Windows:
* install Python3 
* download MicroPython [1] https://micropython.org/download#esp32
* install esptool.py [2] https://github.com/espressif/esptool
* install ampy [3] https://github.com/adafruit/ampy 
<pre>set AMPY_PORT=COM6
ampy ls
AMPY_BAUD=115200</pre>
* connect ESP32 and detect COM port
* erase FLASH - During this phase the BOOT button needs to be pressed down until connection is established.
    <pre>esptool.py --chip esp32 -p /COM6 erase_flash</pre>
* upload Micropython bin: 
    <pre>esptool.py --chip esp32 -p /COM6 write_flash -z 0x1000 ./down/esp32-20180821-v1.9.4-479-g828f771e3.bin</pre>
* Now choose one of these options:
    * [Prepare](https://github.com/octopusengine/octopuslab/blob/master/esp32-micropython/prepare.bat)
<pre>- requires fewer initial files(1)
- copies only files necesarry for initial setup
- finishes quicker than Deploy</pre>
<pre>You **can** pass your port ID (for instance COM3) as first parameter if you're running the script from command line.</pre>
    * [Deploy](https://github.com/octopusengine/octopuslab/blob/master/esp32-micropython/deploy.bat)
<pre>- requires whole directory
- copies all files from root directory, no need for initial setup
- takes longer than Prepare</pre>
<pre>You can pass your port ID (for instance COM3) as first parameter if you're running the script from command line.</pre>
    * webrepl1
    * blockly and webrepl

(1) Files required for Prepare are as follows: (directories included)
 - boot_prepare.py
 - /config/device.json
 - /util/setup.py
 - /util/sys_info.py
 - /util/wifi_connect.py

## Initial setup
* Prepare
    * Once booted in by Putty (or similar software), run setup()
    * run ds (device setting) and choose which board you're using
    * run sw (set wifi) to assign wifi credentials
    * run cw (connect wifi) to reach the internets!
    * run sd (system downloads) to download and apply the rest of files
    
* Deploy
    * Once booted in by Putty (or similar software), run Octopus()
    * run s (setup machine and wifi)
    * run ds (device setting) and choose which board you're using
    * run sw (set wifi) to assign wifi credentials
    * run cw (connect wifi) to reach the internets!