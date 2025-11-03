# 29F160 to UV ERPOM Adapter

Order at your own risk. Untested. 

This board is used to recreate the old UV EPROMs 27C160 and 27C322 with brand new 29F160 EEPROMs. The UV EPROMs are typically only available to purchase used from places like AliExpress and eBay, and are known to arrive damaged or completely inoperable. The 29F160, however, is brand new NOR Flash manufactured by Alliance, for purchase at major electronics distributors.

<a href="https://mou.sr/3HIjb09">Here is a link to the component on Mouser.</a>

With one of these chips, you can make a replacement for the 27C160. With two, you can make a replacement for the 27C322. In fact, with the 29F160's /BYTE pin, you can even make an 8-bit bus version of the 27C322 which was only ever a feature of the 27C160.

![image](https://github.com/user-attachments/assets/954b940d-0a45-4f4b-99c2-4b875b1730a6)

![image](https://github.com/user-attachments/assets/23a340bb-c400-4fa0-b1ad-69484037571b)

All gerbers and source files can be found in this repo, as this project is fully open source. Please read all instructions associated with this board before assembling.

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. You can generally choose whatever thickness you want, but I usually stick to at least 1.0mm. The surface finish can also be whatever you want, but I find ENIG easier to solder the small-pitch parts, personally. Also note that this is a four-layer board.

You can order this board on OSH Park, which is a great option if you only need a small quantity: https://oshpark.com/shared_projects/wLgfzHj1

Alternatively, you can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (NOT YET AVAILABLE) (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station. Drag soldering will be indispensible for this board.
- To program the 29F160 chips, you can use the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a>.

## Programming Adapter

To make programming this board easier, I made this mouthful of an adapter board: the <a href="https://github.com/MouseBiteLabs/29F160-to-UV-EPROM-T48-Programming-Adapter/">29F160 to UV EPROM Programmming Adapter for the T48</a>. It is untested (I haven't received them yet) but if it works, it will let you program both of the 29F160 chips on this breakout board without having to desolder them. You **will still need** the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a> because there's a proprietary EEPROM chip on there to communicate with the main programmer, but this makes it easier nonetheless.

[TO DO: add picture of programming adapter]

## Board Configurations

Most of the configurations are self-explanatory or are described on the back of the board, but here's a breakdown.

### JP1 - 27C160 Mode Jumper

Bridge this solder pad if you are only using one 29F160 chip to replicate a 27C160. Note that this pad is located underneath U4 - meaning you **should not solder JP1 if you have U4 on the board**. U4 is required if you are using two 29F160 chips.

### JP2 - The Byte Mode Jumper

This is a special three-way jumper that sets the mode for the databus output. These sets of pads configures the 29F160's /BYTE pin, which tells the chip to output data in an 8-bit bus or a 16-bit bus. The 27C160 had the same pin feature (as pin 32) but the 27C322 was forced to output a 16-bit bus. Solder the middle-right pad to either the top, bottom, or left according to the following criteria:

- Solder to the bottom to force the data output to be a 16-bit bus. This is how the 27C322 operates natively, and one of the modes the 27C160 can operate in. If you are using two 29F160 chips, then soldering to the bottom pad will produce a drop-in replacement for the 27C322.
- Solder to the top to force the data output to be an 8-bit bus. The 27C160 can output an 8-bit bus, but the 27C322 was never able to!
- Solder to the left to replicate the 27C160 as a drop-in replacement. This is ONLY if you are replicating the 27C160, NOT the 27C322. Soldering to the left will connect the 29F160's /BYTE pin to the through-hole pin 32, which is where the 27C160's /BYTE pin is located. **Do not solder to the left if you are using two 29F160 chips! Pin 32 is the top address pin for switching between the two chips, so it is already in use.**

![image](https://github.com/user-attachments/assets/ddf0554a-106c-4249-8d38-faf8b28501d8)

## The /WE and /RP pins

R1 and R2 are pull-up resistors for /WE and /RP. When in normal operation, these two pins need to be pulled to VCC to operate properly. The pins on the left side of the board are for easy access for potential on-board programming (these are used by the aformentioned <a href="https://github.com/MouseBiteLabs/29F160-to-UV-EPROM-T48-Programming-Adapter/"></a>29F160 to UV EPROM Programmming Adapter for the T48</a>. If you are using this adapter board on one of my cartridges, there may be support for in-circuit programming through these pins. See the repository for the cartridge in question for more information.

## Bill of Materials (BOM): 27C160 (16 Mbit or 2 MB)

| Reference | Value/Part Number | Package | Description      | Source                                           |
| --------- | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| C1        | 0.1uF             | 0603    | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| R1        | 100k              | 0603    | Resistor         | https://mou.sr/49bgMnu                           |
| R2        | 100k              | 0603    | Resistor         | https://mou.sr/49bgMnu                           |
| U2        | M29F160           | TSOP-48 | Flash EEPROM     | https://mou.sr/3HIjb09                           |

## Bill of Materials (BOM): 27C322 (32 Mbit or 4 MB)

| Reference | Value/Part Number | Package  | Description      | Source                                           |
| --------- | ----------------- | -------- | ---------------- | ------------------------------------------------ |
| C1        | 0.1uF             | 0603     | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C2        | 0.1uF             | 0603     | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| R1        | 100k              | 0603     | Resistor         | https://mou.sr/49bgMnu                           |
| R2        | 100k              | 0603     | Resistor         | https://mou.sr/49bgMnu                           |
| U2        | M29F160           | TSOP-48  | Flash EEPROM     | https://mou.sr/3HIjb09                           |
| U3        | M29F160           | TSOP-48  | Flash EEPROM     | https://mou.sr/3HIjb09                           |
| U4        | 74HCT139          | TSSOP-16 | Decoder          | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |

## Revision History

### v2.0 - Release II

- Added /WE and /RP holes for a stronger connection for external programming.
- Added R1 and R2 pull-up resistors to remove the need for soldering/desoldering solder jumpers for switching between programming and operational modes.
  
### v1.2 - Release I

- Added /WE pad (JP3) for experimental on-board programming. Bridging JP3 tied the /WE pin to VCC for normal operation.

### v1.1 - Alpha

### v1.0 - Prototype

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
