# cardreader-kext

## Internal and external USB and PCIe card reader for Mac OSX

Repo ini dibuat sebagai panduan dan referensi bagi yang teman-teman yang ingin mengaktifkan SD Card Reader pada Laptop atau Notebook yang dipakai, baik yang menggunakan USB maupun PCIe.

Telah diuji coba dan berjalan dengan lancar pada :
- Mac OS Siera 10.12.x
- Mac OS High Sierra 10.13.x
- Mac OS Mojave 10.14.x
- Mac OS Catalina 10.15.x
- Mac OS Big Sur 10.15.x

Sebelum melakukan patch :
- File AppleUSBCardReader.kext, yang ada di dalam folder System/Library/Extensions/AppleStorageDriver.kext.
- Lihat Vendor dan Device ID dari perangkat card reader yang dipakai, bisa dengan mempergunakan DPCIManager atau Hackintool. Perhatikan gambar berikut :

![](https://raw.githubusercontent.com/daniasefine/cardreader-kext/main/img/1.png)
![](https://raw.githubusercontent.com/daniasefine/cardreader-kext/main/img/2.png)

Sumber :
- https://noobsplanet.com/index.php?threads/fix-internal-external-card-reader-hackintosh-guide.32/
- Grup Facebook Hackintosh Indonesia
