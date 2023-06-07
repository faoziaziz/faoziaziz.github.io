---
layout: post
title: "Lanjutan kelas Pak Trio : Zynq-7020 Petalinux"
tags:
 - Zynq
---
Oke guys sekarang kita lanjutkan kelas dari Pak Trio yang sudah berakhir.
Kali ini ane akan membuat sebuah development linux dengan menggunakan 
basisframework akselerator DNN UAS kemarin, karena sudah teruji dengan 
menggunakan hardware. 

Petalinux bisa dibuat dengan vitis, pertama harus siapkan xsa dari vivado 
sebelum membuat os dengan petalinux.
```bash
petalinux-create --type project --template zynq --name KeenakanOS
```
kemudian masuk direktorinya
```bash
cd KeenakanOS
```
lalu setting hetting petalinux yang anda buat dengan configurasi file xsa
yang telah anda buat dengan vivado, xsa file saya dibuat dari hasil
kuliah EL-6109 sehingga saya hanya tinggal menggunakan file itu untuk
melanjutkan pembuatan OS_DNN ini.
```bash
petalinux-config --get-hw-description /home/faoziaziz/soc/uas_nn_v2/uasganteng.xsa
```
lalu muncul pada zynq configuration seperti pada 

![gambar](/image/zynq_conf.png)

Pilih berikut pastikan sd card telah terpilih ps7_sd_0 data hal tersebut karena
saya setting boot linuxnya ada pada sdcard pada port sd0
```bash
Subsystem AUTO Hardware Settings  ---> SD/SDIO Settings  ---> Primary SD/SDIO (ps7_sd_0)
```
kemudian exit peta config nanti pilih 
```bash
Subsystem AUTO Hardware Settings  ---> Advanced bootable images storage Settings  ---> 
dtb image settings  ---> image storage media (primary sd)  ---> primary sd
```
kemudian image packaging 
```bash
→ Image Packaging Configuration ---> Root filesystem type (EXT4 (SD/eMMC/SATA/USB))  
---> EXT4 (SD/eMMC/SATA/USB)
```
kemudian konfigurasi kernel
```bash
petalinux-config -c kernel
```
kemudian package 
```bash
petalinux-package --boot --fsbl /intan/soc/peta_uas/zynq_fsbl/fsbl.elf --fpga /home/faoziaziz/soc/uas_nn_v2/uas_nn_v2.runs/impl_1/design_1_wrapper.bit --u-boot
```
kemudian program flash fsbl dan boot.bin yang digenerate. 

Siapkan SDcard, format menjadi 2 bagian yang pertama FAT32 dengan ukuran 60MB yang kedua ext4 
dengan sisa space yang ada.






### Referensi

1. [Hackster Zynq Petalinux](https://www.hackster.io/news/an-fpga-take-on-the-raspberry-pi-petalinux-on-the-zynqberry-67dd421d25aa?fbclid=IwAR1l1ZmnCwhxk3aGbeGyPZGBNChTaLKoGMYXj52ur3QeTc3I8IaV4ZRwI6g)
