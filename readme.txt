Multi-Mapper Cartridge version 1.0
Copyright (c) 2017 Russian Bear Service Crew (RBSC)


IMPORTANT!
IMPORTANT! RBSC does not allow any commercial usage of this cartridge!
IMPORTANT!


The Cartridge
-------------

The Multi-Mapper MSX Cartridge was developed by RBSC to be used commercially, primarily for the shops that
sell MSX games in cartridges. The MM cartridge can emulate all major MSX mappers - Konami4, Konami5, ASCII8
and ASCII16. In addition the cartridge supports the "planar" mode, when the data is presented as a 64kb block.
The cartridge is based on the Altera Max chip (EPM7064SLC44) and includes 512kb FlashROM chip (AM29F040).
The firmware for the cartridge was created by RBSC. It is possible to upgrade the firmware when necessary with
the help of USB Blaster programmer via the JTAG connector.

The benefits of the cartridge include its simple design (only 2 chips and 13 other SMD components), cheap
production, easy maintenance, flexible configuration options and reliability. The cartridge was designed to use
3 different FlashROM chips - TSOP32, PLCC32 and DIP32.


Configuration Jumpers
---------------------

The cartridge is fitted with 5 configuration jumpers. The block of 4 jumpers is used to select the operating mode
and the standalone PRG jumper controls access to the FlashROM chip. The configuration jumpers can be used as
follows:

 * K4 is set, others are not set - Konami4 mapper selected
 * K5 is set, others are not set - Konami5 (SCC) mapper selected
 * A8 is set, others are not set - ASCII8 mapper selected
 * A16 is set, others are not set - ASCII16 mapper selected, default programming mode selected
 * No jumpers are set - planar mode is selected (first 64kb of data is visible)
 * Any 2 jumpers set - disable the cartridge (booting for reprogramming)

The PRG jumper disables detection of the FlashROM if it's set. It's not possible to write any data into the chip
with the installed PRG jumper. To enable reprogramming of the cartridge the PRG jumper must be removed. By default
this jumper must be installed to prevent a game written into the FlashROM to be erased or replaced.


Firmware
--------

There may be a need to update the firmware to fix the earlier found problems. For updating the firmware you need to
have the "USB Blaster" programmer device and a cable to supply 5v onto the cartridge board. The following procedure
should be carried out to update the firmware:

 * Connect +5v to the cartridge board (mind the polarity!)
 * Connect USB Blaster programmer device to a USB port, wait for drivers to be installed
 * Open Quartus II Programmer software
 * Connect the USB Blaster programmer device to the cartridge (mind the markings on the JTAG connector!) and twist
   the connector a bit for better contact with the board
 * In the Quartus software select USB Blaster as the default programming device
 * Click "Autodetect" to detect the installed Altera chip
 * When the chip is detected, put the cursor on the newly-added device string
 * Right click with a mouse and select "Change File"
 * Select the .POF file with the firmware data
 * Enable the checkboxes: "Program/Configure", "Verify" and "Blank Check"
 * Finally click "Start" to start writing the firmware into the Altera chip

If the chip is detected and the firmware is successfully written into it, disconnect the USB Blaster and 5v cable
from the cartridge. In case the chip is not detected, check whether you connected all cables correctly.

WARNING! Do not update the firmware when the cartridge is inserted into the MSX slot! This may result in damages
to the cartridge and MSX computer!


Flashing
--------

The process of writing data into the FlashROM chip is called "flashing". In order to prepare the cartridge to be
programmed, remove the PRG jumper, set both A16 and K4 jumpers, insert the cartridge into MSX slot and power on the
computer. Setting both jumpers will disable the cartridge and allow MSX to boot normally. To be able to program the
cartridge, you need to boot to MSX-DOS or MSX-DOS2 and to use the FL16.COM utility made by GDX. The utility will be
provided with this document.

After the MSX system has booted into DOS, carefully remove the K4 jumper to enable the cartridge's functionality.
Then use the FL16.COM utility to write any suitable ROM file into the cartridge. For example the following command
line can be used:

 FL16 ALESTE.ROM

This command will start the FL16.COM utility, that will try to detect the cartridge, erase the flash chip and write
the file named "ALESTE.ROM" into the cartridge. If there are no errors, then the cartridge is ready to be used. The
only thing necessary is to set the correct mapper type for the loaded ROM file. For example for ALESTE.ROM the
jumper needs to be moved from A16 to K4 - this has to be done only after powering the MSX off and removing the
cartridge from the slot. Finally the PRG jumper needs to be set and the cartridge is ready for use. Just put it
into any MSX slot and power the machine up. The game should start as soon as the MSX accesses the cartridge. If the
game doesn't start, check whether the mapper is set to the correct type for the loaded ROM file.

WARNING! Never insert or remove the cartridge from a cartridge slot when MSX is powered on! This may cause severe
damage to your cartridge or/and MSX computer!

IMPORTANT: The A16 jumper is used not only for setting the ASCII16 mapper, but it's also necessary for programming
of any ROM file into the cartridge with the FL16.COM utility. If you set the jumper to any other mapper
configuration, the FL16 utility will not work correctly.


Precautions
-----------

Please don't use the cartridge if it's damaged, wet, corroded or dirty. This may result in a damage to the cartridge
or/and your MSX computer. If the cartridge no longer works correctly, try to clean the slot pins with white spirit
and a soft cloth. Do not use any solvents on the cartridge! They may damage the mask, the silkscreen and the plastic
casing.


Disclaimer
----------

THE HARDWARE IS PROVIDED “AS IS” AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR
BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR
TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS HARDWARE, EVEN IF ADVISED OF
THE POSSIBILITY OF SUCH DAMAGE.

