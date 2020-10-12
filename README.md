# cardreader-kext

## Internal and external USB and PCIe card reader for Mac OSX - [English](https://github.com/FIRSTPLATO/cardreader-kext/blob/main/README_en.md)

Repo ini dibuat sebagai panduan dan referensi bagi yang teman-teman yang ingin mengaktifkan SD Card Reader pada Laptop atau Notebook yang dipakai, baik yang menggunakan USB maupun PCIe.

Telah diuji coba dan berjalan dengan lancar pada :
- Mac OS Siera 10.12.x
- Mac OS High Sierra 10.13.x
- Mac OS Mojave 10.14.x
- Mac OS Catalina 10.15.x
- Mac OS Big Sur 10.15.x

Sebelum melakukan patch :
- File [AppleUSBCardReader.kext](https://github.com/ares-x45c/cardreader-kext/blob/main/kext/AppleUSBCardReader.kext.zip), yang ada di dalam folder System/Library/Extensions/AppleStorageDriver.kext.
- File [Sinetek-rtsx.kext](https://github.com/ares-x45c/cardreader-kext/blob/main/kext/Sinetek-rtsx.kext.zip). *Hanya diperlukan apabila mempergunakan Vendor Realtek PCIe versi lama
- Lihat Vendor dan Device ID dari perangkat card reader yang dipakai, bisa dengan mempergunakan DPCIManager atau Hackintool. Perhatikan gambar berikut :

![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/1.png)
![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/2.png)
> yang di-highlight ungu itu adalah Vendor dan Device ID nya, misal pada gambar di atas, yang dipakai adalah 10EC dan 5289.

Cara melakukan patch :
- Cukup buka dan edit file AppleUSBCardReader.kext/Contents/Info.plist, bisa pakai aplikasi seperti Plist Editor Pro, atau yang lain.
- Search IOKitPersonalities > AppleSDCardReader > Physical Interconnect Location > lalu edit Physical Interconnect Location value section sebagai External.
- Search Vendor Identification dan ubah value section ke "Generic Reader"
- Search Apple_Internal_SD_Card_Reader_1_00 dan edit string value idProduct dan idVenedor ke desimal, pakai Product ID and Vendor ID yang didapat sebelumnya, tapi ubah dulu ke desimal, pakai calculator scientific.
- Search Apple_Internal_SD_Card_Reader_2_00 dan edit string value idProduct dan idVendor ke desimal. (Sama persis seperti langkah sebelumnya)
- Pastikan untuk mengubah semua value ke Physical Interconnect Location pada Apple_internal_SD_Card_Reader_1_00 dan Apple_Internal_SD_Card_Reader_2_00 ke External
- Simpan AppleStorageDriver.kext siap digunakan langsung pada Clover maupun Opencore, tanpa perlu inject ke S/L/E dan L/E.

![](https://raw.githubusercontent.com/FIRSTPLATO/cardreader-kext/main/img/3.png)
> Hasil kext yang telah dipatch secara manual untuk Realtek RTL8411 pada Asus X45C, bekerja dengan sempurna.

Sumber :
- https://noobsplanet.com/index.php?threads/fix-internal-external-card-reader-hackintosh-guide.32/
- Grup Facebook Hackintosh Indonesia
