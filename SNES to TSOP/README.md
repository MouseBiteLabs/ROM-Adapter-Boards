# SNES Mask ROM to TSOP

This board lets you use 29F016 or 29F032/29F033 TSOP EEPROMs to place in the SNES mask ROM socket on original SNES boards (or my [Basic UV boards](https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/tree/main/Basic%20UV)). You can also use two 29F016 chips (generally less expensive than the 29F033) to make a full 32 Mbit (4 MB) game.

![image](https://github.com/user-attachments/assets/e3e41465-150b-48e1-b731-0d86074a814a)

![image](https://github.com/user-attachments/assets/ebf83b39-1fc4-49f6-b858-4743c5f8f3ba)

All gerbers and source files can be found in this repo, as this project is fully open source. Please read all instructions associated with this board before assembling. **This design is intended for personal use only, not for modifying existing cartridges for commercial sale.** I really would rather you *not* use these adapter boards to repurpose old carts into rarer games or ROM hacks in order to sell them commercially.

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. You can generally choose whatever thickness you want, but I usually stick to at least 1.0mm. The surface finish can also be whatever you want, but I find ENIG easier to solder the small-pitch parts, personally. Also note that this is a four-layer board.

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!)

<a href="https://mousebitelabs.etsy.com/listing/1252691381"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can order this board on OSH Park, which is a great option if you only need a small quantity: https://oshpark.com/shared_projects/ZvoKSwja

Alternatively, you can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (NOT YET AVAILABLE) (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station. Drag soldering will be indispensible for this board.
- To program the 29F016 or 29F032/29F033 chips, you can use the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a>.

## Programming Adapter

Coming soon.

## The /WE Pads

The right side of the pads marked /WE connects to the write enable pin of the TSOP(s). You can run a wire from the right pad to the /WR pin of your cartridge to use in a cart edge programmer (if the chips are supported). If you are not using this capability, then bridge the two pads with solder.

## Board Configuration #1 - 16 Mbit (or 2 MB)

If your game is 16 Mbit or smaller, then use one 29F016 on the top TSOP footprint. Solder bridge the /CS pads within the 74'139 footprint. Please note the pin 1 indicator for the TSOP is on the bottom right corner.

### Bill of Materials (BOM): Configuration #1

| Reference | Value/Part Number | Package | Description      | Source                                           |
| --------- | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| Top TSOP  | 29F016            | TSOP-48 | Flash EEPROM     | AliExpress, eBay                                 |

## Board Configuration #2 - 32 Mbit (or 4 MB) with the 29F032/29F033

If you want to make a game larger than 16 Mbit (up to 32 Mbit) you can use one 29F032/29F033 in place of the 29F016 described in the previous section. Again, bridge the /CS pads. Note that because this chip is (normally) 40-pins, you have to center it such that the outside pair of pins on each corner are empty, as shown below:

![image](https://github.com/user-attachments/assets/580d0409-1f65-4351-b904-344e453a6054)

### Bill of Materials (BOM): Configuration #2

| Reference | Value/Part Number | Package | Description      | Source                                           |
| --------- | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| Top TSOP  | 29F032/29F033     | TSOP-48 | Flash EEPROM     | AliExpress, eBay                                 |

## Board Configuration #3 - 32 Mbit (or 4 MB) with 2x 29F016

Finally, if you want to make a larger game with two 29F016 chips, you will need to populate both TSOP footprints, the 74'139 decoder, in addition to adding a solder bridge on the "PLAY" pads on the left of the board.

![image](https://github.com/user-attachments/assets/2e492008-9988-4ae6-b834-9bdd872eb40e)

### Bill of Materials (BOM): Configuration #3

| Reference    | Value/Part Number | Package | Description      | Source                                           |
| ------------ | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| Top TSOP     | 29F016            | TSOP-48 | Flash EEPROM     | AliExpress, eBay                                 |
| Bottom TSOP  | 29F016            | TSOP-48 | Flash EEPROM     | AliExpress, eBay                                 |
| 74'139       | 74HCT139          | SOIC-16 | Decoder          | [https://mou.sr/48Dk8As](https://mou.sr/48Dk8As) |

## Revision History

### v1.4 - Re-release

- Ported from Eagle to KiCad

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
