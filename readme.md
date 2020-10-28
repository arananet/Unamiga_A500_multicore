# Unamiga A500 Header and Unamiga Reloaded Cores.

This repository contains all the cores available for the Unamiga A500 Header and Unamiga Reloaded boards. All of them includes two extensions, one is JIC for using permatelly on the fpga (only recommended when you dont have the multicore onboard) and the UA2 extension which must be used for the multicore support. All of them are compatible with next boards:

### Unamiga A500 1.4 (with multicore hat)
### Unamiga A500 1.5

Browse the CORES directory to download the required one.

### Permanent Firmware vs Multicore support:

If you don't have the multicore support you can use the JIC files to permatelly burn the new core on the FPGA. In order to do this you will require a USB BLASTER and the QUARTUS 13.1 software.

USB BLASTER example (recommended for both, permatelly and multicore support):

https://es.aliexpress.com/item/4000428690459.html?spm=a2g0o.productlist.0.0.56eeaa6csAYyPO&algo_pvid=6985defa-48ba-4692-abb4-307d74d6e8df&algo_expid=6985defa-48ba-4692-abb4-307d74d6e8df-11&btsid=0b0a182b16038866260806565e01e2&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_

### How the Multicore works?

There two versions of the multicore solution for the Unamiga A500. For the 1.4 board, a HAT board has been specially designed. This board has an STM32 onboard with a RAM module required for some cores. The Unamiga 1.5 uses a STM32 bluepill board to provide the same function. The RAM module is already available on the 1.5 version.

The STM32 bluepill is not provided on the Unamiga 1.5, there is a footprint on the board to add it (soldering is required), a link with a stm32 bluepill module with the stlink for flashing it is provided on the next link (also remember, is required to also have a USB BLASTER):

https://es.aliexpress.com/item/1005001636595415.html?spm=a2g0o.productlist.0.0.499f782eQoVCgo&algo_pvid=87b0f95e-dd06-4701-abd4-6e29825084b6&algo_expid=87b0f95e-dd06-4701-abd4-6e29825084b6-2&btsid=0b0a556e16038874338337501e6fca&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_

Also in order to connect the stm32 on the FPGA in the Unamiga 1.5 you will require a little IDC 2x5 female to female cable link this one:

https://es.aliexpress.com/item/32700048506.html?spm=a2g0o.productlist.0.0.310b601fW3osbp&algo_pvid=af77932d-76d4-4b9a-b921-a23483ff0068&algo_expid=af77932d-76d4-4b9a-b921-a23483ff0068-8&btsid=0bb0623e16038875348986088ed701&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_

In both cases (1.4 and 1.5) you will require an additional SD card to store each core in UA2 format. You just download each core in UA2 format from the CORES folder and drop them on the root of the multicore sd card. Also the STM32 requires an special firmware and core. On the Unamiga 1.4 header, the Firmware made by Victor Trucco needs to be burned on the STM32 bluepill (on the 1.4 version is already burned) that goes onboard. Also the stm32 requires a core that must be flashed on the FPGA (this is why we need the USB BLASTER). On the CORES/MULTICORE folder there is a JIC file that's the one we need to flash on the FPGA. By doing this, the fpga always will run the multicore core and will replace the one that was burned before.

Remeber, some cores requires another SD card because their special filesystem, so make sure you put the correct SD card on the FPGA socket (the one on the back) with the SD that will be used for the selected core.

### Flashing the STM32 (only for 1.5 headers)

In order to flash the multicore firmware from Victor Trucco on the 1.5 header, you will need to download the STM32Cubeprogrammer (requires the STLINK usb).

https://www.st.com/en/development-tools/stm32cubeprog.html

1-Install the Cubeprogrammer software.

2-Download the multicore bin file from the CORES/MULTICORE folder.

3-Connect the STLINK to the STM32 bluepill board on the required pins following the next schematic:

<img src="https://www.botnroll.com/img/cms/connections.png" width="350" title="Image taken from https://www.botnroll.com/img/cms/connections.png">

4-Connect to your computer and open the Cube programmer software.

5-Click on the CONNECT buttom from the right panel. If everything is OK it will connect and you will see a log update on the main screen. Select the Open File TAB and choose the BIN file downloaded from this github. Then git the DOWNLOAD button and the STLINK will start programming the core.

Note: Since we are using the STLINK we don't need to change the JUMPERS from the STM32.

Once it finish, you well see a DOWNLOAD COMPLETE on the main log screen.

If everything goes like these instructions, you have succefully setted up the STM32 bluepill board.

### Flashing the multicore core (this is required for BOTH versions of the UNAMIGA A500 header).

In order to flash the multicore core on the FPGA we will need the USB BLASTER and the QUARTUS PROGRAMMING SOFTWARE. Follow the next instructions to properly setup it.

1-Download and install the Altera Quartus 13.1:

https://fpgasoftware.intel.com/13.1/

2-Download the multicore core JIC file from the CORES/MULTICORE folder.

3-Connect the USB BLASTER on your computer, also connect the USB BLASTER using the IDC connector on the FPGA of the UNAMIGA header (the black board) make sure you connect it properly. Powerup the UNAMIGA header.

4-Open the QUARTUS program, make clic on the ADD FILE button, browse to the folder where you you download the JIC file and choose it. Select the two check box button (marked on the image).

5-Finally hit the START button to start flashing the new core. You will see that the progress bar will start increasing. Once it's at the 100% you will have the new core burned permatelly on the FPGA. Finally if it hits the 100%, disconnect the USB blaster from the UNAMIGA header and  connect the IDC from the HEADER to the FPGA.

If all goes OK turn on the UNAMIGA header and you will see a blue little window with the cores that you have downloaded from the step before.

Once we got all setted up, with the stm32 flashed, the fpga with the multicore flashed, the sd card on the multicore socket, the IDC little cable connected, powerup the unamiga header and you will see the cores in a list. To select the required core to start using that machine/console, use the ARROW keys and ENTER to choose the required one.


### SD cards distribution: 

Usually each core requires to have the SD card for the FPGA with his own filesystem, for example the MSX and the SPECCY (next) cores. The MINIMIG (AMIGA) SD could coexist with others like NES or C64.

### MINIMIG:
Requires the provided FREE SD card with the UNAMIGA.

### C64 core:
You can use the MINIMIG core SD, just create a new folder on the root called C64 and put all the prg or taps inside.

### NES core:
You can use the MINIMIG core SD, just create a new folder on the root called NES and put all the roms.

### MSX core:
Requires a custom SD card because his partitions configurations. The SD image required for the core can be downloaded from here: https://www.zxuno.com/forum/viewtopic.php?t=3976.

### ZXNEXT core:
Requires a custom SD card because his partitions configurations. The SD image required for the core can be download from the original project, here: https://www.specnext.com/latestdistro/

# Special thanks

Thanks to @benitoss for porting the ZXNEXT and MSX cores.

Thanks to Neuro for porting the C64 and the NES cores.

Thanks to Victor Trucco for create the multicore system.

Thanks to the Unamiga users that has been a huge support to keep this project alive.

