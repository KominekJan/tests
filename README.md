## Windows:
* install Python3 - https://www.python.org/downloads/
* download MicroPython - https://micropython.org/download#esp32
* install esptool - https://github.com/espressif/esptool
* install ampy - https://github.com/adafruit/ampy
* connect ESP32 and detect COM port
* erase FLASH - During this phase the BOOT button needs to be pressed down until connection is established.
    <pre>esptool.py --chip esp32 -p /COM6 erase_flash</pre>
* upload Micropython bin: 
    <pre>esptool.py --chip esp32 -p /COM6 write_flash -z 0x1000 ./down/esp32-_FileVersion_.bin</pre>
* Now choose one of these options:
    * [Prepare](https://github.com/octopusengine/octopuslab/blob/master/esp32-micropython/prepare.bat)
        <pre>  - requires fewer initial files(1)
        - copies only files necesarry for initial setup
        - finishes quicker than Deploy</pre>
        <pre>You can pass your port ID (for instance COM3) as first parameter if you're selectning the script from command line.</pre>
    * [Deploy](https://github.com/octopusengine/octopuslab/blob/master/esp32-micropython/deploy.bat)
        <pre>  - requires whole directory
        - copies all files from root directory, no need for initial setup
        - takes longer than Prepare</pre>
        <pre>You can pass your port ID (for instance COM3) as first parameter if you're selectning the script from command line.</pre>
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
    * Once booted in by Putty (or similar software), select setup()
        <pre>
        ==============================
                S E T U P
        ==============================
         [ds]  - device setting
         [sw]  - set wifi
         [cw]  - connect wifi
         [st]  - set time
         [sd]  - system download >
         (initial octopus modules)
         [si]  - system info
         [e]   - exit setup
        ==============================</pre>
    * select ds (device setting) and choose which board you're using
    * select sw (set wifi) to assign wifi credentials
    * select cw (connect wifi) to reach the internets!
    * select sd (system downloads) to download and apply the rest of files
    
* Deploy
    * Once booted in by Putty (or similar software), select Octopus()
        <pre>
        ==============================
          O C T O P U S    M E N U
        ==============================
         SYSTEM & SETTINGS
         [i] - device & system info
         [s] - setup machine and wifi
         [w] - wifi test
         [f] - file info/dir
         [c] - clear terminal
        ==============================</pre>
    * select s (setup machine and wifi) to open further options (same menu as in Prepare)
    * select ds (device setting) and choose which board you're using
    * select sw (set wifi) to assign wifi credentials
    * select cw (connect wifi) to reach the internets!
    

## File structure

<pre>

root
 ╟─boot.py
 ╟─main.py
 ╚╦═assets
  ╠═config (json config files - device/wifi/...)
  ║
  ╠═lib
  ║
  ╠═pinouts (boards and soc type)
  ║
  ╠═util╦═setup
  ║     ╠═led/buzzer
  ╠═... ╠═...
</pre>