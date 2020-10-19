# cardreader-kext

## Internal and external USB and PCIe card reader for Mac OSX - [Bahasa Indonesia](https://github.com/FIRSTPLATO/cardreader-kext)

This repo was created for refference and turorial for you which are wanna to activate SD Card Reader on your Laptop / Notebook, support USB and PCIe based card reader.

Tested and working well on :
- Mac OS Sierra 10.12.x
- Mac OS High Sierra 10.13.x
- Mac OS Mojave 10.14.x
- Mac OS Catalina 10.15.x
- Mac OS Big Sur 10.16.x

Before doing patch :
- File [AppleUSBCardReader.kext](https://github.com/ares-x45c/cardreader-kext/blob/main/kext/AppleUSBCardReader.kext.zip), in folder System/Library/Extensions/AppleStorageDriver.kext.
- File [Sinetek-rtsx.kext](https://github.com/ares-x45c/cardreader-kext/blob/main/kext/Sinetek-rtsx.kext.zip). *Just needed if your hardware using old version Realtek PCIe as vendor. 
- just take a look for Vendor and Device ID from your card reader, you can use tools like DPCIManager or Hackintool. You can see screenshot below :

![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/1.png)
![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/2.png)
> purple highlighted are Vendor and Device ID, as example on the screenshot above, are 10EC and 5289.

How to do patch :
- Just open and edit file AppleUSBCardReader.kext/Contents/Info.plist, you can use tools like Plist Editor Pro, or prefer your other editor.
- Search IOKitPersonalities > AppleSDCardReader > Physical Interconnect Location > an then edit Physical Interconnect Location value section as External.
- Search Vendor Identification and change value section to "Generic Reader"
- Search Apple_Internal_SD_Card_Reader_1_00 and edit string value idProduct and idVenedor to decimal, use Product ID and Vendor ID that we just got above, but change it to decimal first, you can use scientific calculator.
- Search Apple_Internal_SD_Card_Reader_2_00 and edit string value idProduct and idVendor to decimal. (Same as to be done on above step)
- Ensure to change all value to Physical Interconnect Location on Apple_internal_SD_Card_Reader_1_00 and Apple_Internal_SD_Card_Reader_2_00 to External
- Save AppleStorageDriver.kext, it is alreay to be use directly with Clover or Opencore, without needed inject to S/L/E and L/E.

![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/3.png)
> After manual patch for Realtek RTL8411 on Asus X45C, working well.

If you need help to patch your card reader (totally free), please :
- Create new issue on https://github.com/FIRSTPLATO/cardreader-kext/issues, with title format #Request-Patch-your_name, and don't forget to give attachment  Vendor and Device ID from DPCIManager or Hackintool.
- or via WhatsApp to [08999-302-702](https://wa.me/628999302702), also with screenshot of DPCIManager or Hackintool, for Vendor and Device ID.

Source :
- https://noobsplanet.com/index.php?threads/fix-internal-external-card-reader-hackintosh-guide.32/
- Grup Facebook [Hackintosh Indonesia](https://web.facebook.com/groups/hackintosh.indonesia)

Feel free to reach us on :
- https://www.firstplato.com
- https://www.facebook.com/firstplato
- admin@firstplato.com
