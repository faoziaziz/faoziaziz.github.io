---
layout: post
title: "Das U-boot"
tags:
 - Diary
background: '/img/bg-about.jpg'
---
# Das U-boot Problem
Das U-boot yang sebelumnya sukses di loading sekarang justru mengalami error yang tidak bisa saya perbaiki

```shell
U-Boot 2022.01 (Sep 20 2022 - 06:35:33 +0000)

CPU:   Zynq 7z020
Silicon: v3.1
Model: Zynq ZC702 Development Board
DRAM:  ECC disabled 1 GiB
initcall sequence 3ffd22d4 failed at call 040028bc (err=-19)
### ERROR ### Please RESET the board ###
```
padahal sebelemunya bisa, lets we start this journey

## Boot package evaluation 
saya menggunakan command berikut untuk tidak mempackage fsbl dan bitstream unutk melakukan evaluasi error terjadi karena effect overlap antara fsbl dan bitstream.
```bash
petalinux-package --boot --u-boot --force
```
hasilnya sungguh mengejutkan memang tidak error di uboot, maksudnya error di das u boot tidak membelikan log error namun tidak bisa masuk ke dalam boot kernel.

## Menambahkan Fsbl dalam boot bin
harapannya setelah menambahkan command ini saya bisa melakukan bootloading ke rootfs
```shell
petalinux-package --boot --fsbl zynq_fsbl.elf --u-boot --force 
```
dan melakukan communikasi uart
```bash
picocom /dev/ttyUSB0 --baud 115200 --omap crcrlf
```
ternyata bootloading tidak mengalami perubahan. 

Mungkin ini masalah configurasi hardware setting pada vivado, mungkin juga masalah file kernel nya, saya masih menguji beberapa command siapa tahu memang benar ada di kernelnya karena saya pernah berhasil melakukan booting hingga rootfs. 

## Oke kita kembali ke state awal
Package boot dengan semuanya
```bash
petalinux-package --boot --fsbl zynq_fsbl.elf --u-boot --fpga system.bit --force 
```



