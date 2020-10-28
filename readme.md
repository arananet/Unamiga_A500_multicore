# Unamiga A500 Header and Unamiga Reloaded Cores.

This repository contains all the cores available for the Unamiga A500 Header and Unamiga Reloaded boards. All of them includes two extensions, one is JIC for using permatelly on the fpga (only recommended when you dont have the multicore onboard) and the UA2 extension which must be used for the multicore support. All of them are compatible with next boards:

### Unamiga A500 1.4 (with multicore hat)
### Unamiga A500 1.5

Browse the CORES directory to download the required one.

### SD cards distribution: 

Usually each core requires to have the SD card for the FPGA with his own filesystem, for example the MSX and the SPECCY (next) cores. The MINIMIG (AMIGA) SD could coexist with others like NES or C64.

### MINIMIG:  Requires the provided FREE SD card with the UNAMIGA.
### C64 core: You can use the MINIMIG core SD, just create a new folder on the root called C64 and put all the prg or taps inside.
### NES core: You can use the MINIMIG core SD, just create a new folder on the root called NES and put all the roms.
### MSX core: Requires a custom SD card because his partitions configurations. Find a SD card image on the MSX directory.
### ZXNEXT core: Requires a custom SD card because his partitions configurations.

# Special thanks

Thanks to @benitoss for porting the ZXNEXT and MSX cores.
Thanks to Neuro for porting the C64 and the NES cores.
Thanks to Victor Trucco for create the multicore system.
Thanks to the Unamiga users that has been a huge support to keep this project alive.
