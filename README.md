# Super Game Boy MBC5 Cartridge - UNDER CONSTRUCTION DO NOT READ

Have you ever seen a standalone Pokemon Red cartridge for the *Super Nintendo*? The usual way of making one of these is to take a Super Game Boy and a Game Boy cartridge, and permanently solder the Game Boy cartridge to the Super Game Boy cartridge, and put it into a shell. But it doesn't have to be this way!

This circuit board integrates an MBC5 Game Boy game *into* a Super Game Boy cartridge, for a cleaner look and install. The PCB itself can fit inside most (if not all) Super Nintendo cartridge shells without any trimming required, other than the trimming needed on the bottom of standard SNES shells that didn't have openings for the expansion pins the Super Game Boy (and other games with co-processors) have. The features are as follows:

- Able to make games up to 2 MB of ROM size
- Able to utilize up to 256 KB of RAM using an FRAM chip (no backup batteries required)
- Fixed clock speed, or compatible with qwertymodo's clock mod that retains functionality with Hori's game pad for overclocking and underclocking
- Restored link port functionality

[pictures]

All gerbers and source files can be found in this repo, as this project is fully open source. Technical documentation of the board can be found in the Technical folder.

## Important Things Before You Start

1) To use this board, you need to have an original Game Boy game that uses an MBC5 mapper chip. <a href="https://catskull.net/gb-rom-database/">You can find a list of games and their mappers here</a>. Use the search function.
2) You will need to remove the MBC5 from your donor cartridge for use on this board. This will require a hot air rework station or a hot plate. There's a list below of other parts you can re-use from the donor cartridge.
3) You will also need to remove various chips from an origial Super Game Boy cartridge. The Japanese Super Game Boy boards will work, but **Super Game Boy 2 is not compatible**.
4) When soldering parts on, it's a good idea to put kapton tape or otherwise cover the bottom cartridge edge. You do not want to get solder on the cartridge contacts.
5) I am not responsible for any damage you do to your self or your property. Attempt this project at your own risk.
6) I do not guarantee design compatibility. You may encounter issues with certain games. There is also a chance I have made an error in the design or the BOM - if this is the case, I will do everything I can to address the problem as quickly as possible.
7) If you are using this board to make games other than for personal use, you must have permission from the originator to use and distribute any ROM images or other related material. You are responsible for making sure you adhere to any license requirements.

DO NOT use my circuit boards for profiting from stolen work - this especially includes homebrew content, ROM hacks, and using fan-made labels without permission from the originator. **Support original creators!**

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. The following options **must** be chosen when ordering boards for yourself.

- Thickness: 1.2mm
- Surface Finish: ENIG
- Gold Fingers: Yes, 30° chamfer

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/project/shareproject/Game_Boy_MBC5_Cartridge_b98d04df.html"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

Equipment

## Board Configurations

Talk about configurations

### SRAM Size Selection (SJ1 and SJ2, or SW1)

These jumpers are located underneath the MBC5 chip, and labeled "64K" and "256K/1M". Solder them to configure the amount of RAM your cart uses. You must configure these pads for every game you make, unless you do not need RAM. <a href="https://catskull.net/gb-rom-database/">You can find a list of games here with their respective RAM sizes.</a>

- If the game you're making uses 256 Kbit or 1 Mbit of RAM, then solder the middle pads of the two jumper sets to the right pads.
- If the game you're making uses 64 Kbit of RAM, then solder the middle pads of the two jumper sets to the left pads.
- SJ1 and SJ2 must be soldered in the same direction.
- The footprint of these selection pads should allow for a DPDT switch, part number CAS-220A1, to be placed on these pads instead of having to bridge the pads with solder.

Note that you can make games that only require 64 Kbit of RAM and still use a 256 Kbit or 1 Mbit SRAM chip. You still need to configure the jumpers to the 64Kb setting, though.

**I recommend using 64 Kbit or 256 Kbit RAM chips, unless you absolutely need 1 Mbit for the game you are making.**

### Using an MM1134 or BA6735 for U4 (SJ3)

Bridge the jumper SJ3 if you have either an MM1134 or BA6735 for U4, specifically. Any other battery management IC must leave SJ3 unsoldered.

## Bill of Materials (BOM)

Your parts list will vary depending on the game you are trying to make, and what chips you have for the battery management (if any). **You cannot use both U4 and U5 - you must choose one or the other.** U4 comes from a donor cartridge, and U5 is a readily available aftermarket option.

Please carefully review the parts you need for the board you are trying to make. Do not add any parts to your build that don't appear in the column for the game you are making. This means you *cannot* populate every component on the board at the same time.

| Reference Designators | Value/Part Number              | Package          | Description        | No save carts | Save carts with MM1134 or BA6735 | Save carts with MM1026 or BA6129 | Save carts without donor U4 chip | Source                                           |
| --------------------- | ------------------------------ | ---------------- | ------------------ | ------------- | -------------------------------- | -------------------------------- | -------------------------------- | ------------------------------------------------ |
| B1                    | CR2032, CR2025, CR2016         | CR2032           | Backup Battery     |               | X                                | X                                | X                                | [https://mou.sr/3SeAzfT](https://mou.sr/3SeAzfT) |
| C1                    | 0.1uF                          | 0603             | Capacitor (MLCC)   | X             | X                                | X                                | X                                | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C4                    | 0.1uF                          | 0603             | Capacitor (MLCC)   | X             | X                                | x                                |                                  | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C5                    | 0.1uF                          | 0603             | Capacitor (MLCC)   |               | X                                | X                                | X                                | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C6                    | 10uF                           | 0603             | Capacitor (MLCC)   |               | X                                | X                                | X                                | [https://mou.sr/3mZtSkF](https://mou.sr/3mZtSkF) |
| C7                    | 0.1uF                          | 0603             | Capacitor (MLCC)   | X             | X                                | X                                | X                                | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C8                    | 0.1uF                          | 0603             | Capacitor (MLCC)   |               |                                  |                                  | X                                | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| Q1                    | 2N7002                         | SOT-23           | N-Channel FET      |               |                                  |                                  | X                                | [https://mou.sr/3rgfh6J](https://mou.sr/3rgfh6J) |
| Q2                    | 2N7002                         | SOT-23           | N-Channel FET      |               |                                  | X                                |                                  | [https://mou.sr/3rgfh6J](https://mou.sr/3rgfh6J) |
| R1                    | 10k                            | 0603             | Resistor           |               | X                                | X                                | X                                | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R7                    | 10k                            | 0603             | Resistor           |               |                                  | X                                |                                  | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R8                    | 10k                            | 0603             | Resistor           | X             | X                                | X                                | X                                | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R9                    | 130k                           | 0603             | Resistor           |               |                                  |                                  | X                                | [https://mou.sr/3MjXliy](https://mou.sr/3MjXliy) |
| R10                   | 49.9k                          | 0603             | Resistor           |               |                                  |                                  | X                                | [https://mou.sr/3Q3NRZO](https://mou.sr/3Q3NRZO) |
| U1                    | 29F016, 29F032, 29F033         | TSOP-48, TSOP-40 | Flash EEPROM       | X             | X                                | X                                | X                                | AliExpress or eBay                               |
| U2                    | MBC5                           | QFP-32           | MBC5 Mapper        | X             | X                                | X                                | X                                | Donor MBC5 Game Boy cartridge                    |
| U3                    | AS6C6264, AS6C62256, AS6C1008  | SOP-28, SOP-32   | SRAM               |               | X                                | X                                | X                                | [https://mou.sr/3ZxG6jd](https://mou.sr/3ZxG6jd) |
| U4                    | MM1026, MM1134, BA6129, BA6735 | SOIC-8           | Battery Management |               | X                                | X                                |                                  | Donor Game Boy cartridge                         |
| U5                    | TPS3613                        | MSOP-10          | Battery Management |               |                                  |                                  | X                                | https://mou.sr/45Ir2kh                           |

## Things to Remember

- The footprint for the EEPROM is specifically for 29F016 - it has 48 pins. However, 29F032 and 29F033 are only 40 pin devices. They still work fine on the board though - place them in the center of the footprint, and leave the outer two pins on each corner empty
- The 29F016, 29F032, and 29F033 have been known to occasionally be defective upon arrival. They're either used, or new old stock, and usually only available from AliExpress.
- The footprint for the battery can fit a CR2032, CR2025, or CR2016 with solder tabs. The only difference is the mAh capacity (larger number = longer life). If you get Panasonic tabbed batteries, you may have to trim the battery tabs to make them fit on the footprint.
  - For untabbed coin cells, you can find battery retainer adapters online, <a href="https://retrogamerepairshop.com/products/hdr-game-boy-game-battery-retainer?variant=40511013290156">like this one,</a> but only for board revision v1.4. It will not fit on earlier revisions.
- For battery management, use either U4 *or* U5 and supporting components. **Do not** use U4 and U5 simultaneously on one board. They will interfere with each other.
- Generally, ROM sizes are conveyed in terms of kilo**bytes** and mega**bytes** (KB, MB). RAM size is usually conveyed in terms of kilo**bits** or mega**bits** (Kbit, Mbit). You can convert Kbit and Mbit to KB and MB by dividing Kbit or Mbit by 8. For example, 256 Kbit = 32 KB.
- You only need to provide ROM and RAM chips that have at least *or greater* the size of the game you are trying to make. That means you can use a 256 Kbit SRAM chip for a game that only requires 64 Kbit of RAM!

## Labels

Labels

## Revision History

### v1.0
- Release revision

## Resources and Acknowledgements
- <a href="https://github.com/Gekkio/gb-schematics">Gekkio's Game Boy schematics</a> - *huge* thanks for the SGB schematics specifically, as it saved me so much time on this project
- <a href="https://gbhwdb.gekkio.fi/">Game Boy Hardware Database</a>
- <a href="https://catskull.net/gb-rom-database/">Nintendo Gameboy Game List</a>
- <a href="https://www.gbxcart.com/">insideGadgets discord server for FRAM compatibility requirements</a>

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2024
