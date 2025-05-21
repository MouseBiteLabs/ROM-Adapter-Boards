# 29F160 to UV ERPOM Adapter

Order at your own risk. Untested. 

This board is used to recreate the UV EPROMs 27C160 and 27C322 with brand new 29F160 EEPROMs. Include 1x 29F160 and bridge JP1 with solder to emulate a 27C160, or use 2x 29F160 and populate U4 for a 27C322.

The databus is controlled by JP2, for 8 bit mode or 16 bit mode. This means you can have a 27C322 act in 8 bit mode - something the original chip did not support.

Version 1.2 added /WE pads via JP3. The right-side pad is connected to the /WE pins of the two ROM chips, the left-side pad is connected to VCC. You can wire the /WE pad to an external point to attempt programming the 29F160 on the adapter board. Otherwise, short JP3 with a solder pad.

OSH Park: https://oshpark.com/shared_projects/Rcthkw3s

29F160: https://www.mouser.com/ProductDetail/Alliance-Memory/M29F160FT55N3E2?qs=vmHwEFxEFR%252BPKObcaS0Aqw%3D%3D

![image](https://github.com/user-attachments/assets/e3de07ee-5d22-4e2a-9c12-4dd214c6794f)

![image](https://github.com/user-attachments/assets/2a68fc93-3039-46de-8df6-94263e047fad)

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
