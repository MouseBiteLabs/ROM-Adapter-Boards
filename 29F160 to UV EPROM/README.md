# 29F160 to UV ERPOM Adapter

Order at your own risk. Untested. 

This board is used to recreate the UV EPROMs 27C160 and 27C322 with brand new 29F160 EEPROMs. Include 1x 29F160 and bridge JP1 with solder to emulate a 27C160, or use 2x 29F160 and populate U4 for a 27C322.

The databus is controlled by JP2, for 8 bit mode or 16 bit mode. This means you can have a 27C322 act in 8 bit mode - something the original chip did not support.

Version 1.2 added /WE pads via JP3. The right-side pad is connected to the /WE pins of the two ROM chips, the left-side pad is connected to VCC. You can wire the /WE pad to an external point to attempt programming the 29F160 on the adapter board. Otherwise, short JP3 with solder.

Version 2.0 added /WE and /RP holes on the left side, with pull-up resistors near the top ROM chip. This prevents the need for shorting the pads, and provides a stronger connection for wires from /WE and /RP for programming.

OSH Park: https://oshpark.com/shared_projects/V4uznOwT

29F160: https://www.mouser.com/ProductDetail/Alliance-Memory/M29F160FT55N3E2?qs=vmHwEFxEFR%252BPKObcaS0Aqw%3D%3D

![image](https://github.com/user-attachments/assets/925b8f41-b223-4731-a35a-ac4e0c8b8ba7)

![image](https://github.com/user-attachments/assets/bc70df83-e80e-4e00-baab-a9591a2f0baa)

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
