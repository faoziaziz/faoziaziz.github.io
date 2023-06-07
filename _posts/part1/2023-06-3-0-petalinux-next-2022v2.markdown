---
layout: post
title: "Petalinux 2022v2"
tags:
 - Diary
background: '/img/bg-about.jpg'
---
Perintah untuk membuat sebuah project dengan petalinux
```bash
petalinux-create --type project --template zynq --name myir_test
```
untuk mendapatkan path .xsa file
```
petalinux-config --get-hw-description ../../../xilinxTest/purbalingga/board_design_wrapper.xsa
```

diatas sepertinya tidak cocok dengan configurasi dengan petalinux 2021 v1. 

Aku mencoba menggabungkan dengan chatGPT jadi data yang masuk ke chat gpt hanya bisa mencakup 2021 kebawah.

dengan menggunakan bantuan chat gpt kita bisa membuat tipe 2021v1 kompactible dengan command berikut

```bash
petalinux-create -t project -s ./../../xilinxTest/purbalingga/board_design_wrapper.xsa --name v21ujicoba
```
```bash
petalinux-boot --jtag --u-boot --hw_server-url localhost:3121
```
Format SDCARD

```bash
sudo mkfs.vfat -n 'BOOT' -I /dev/sda1
sudo mkfs.ext4 -n 'ROOTFS' -I /dev/sda2
```

```bash
petalinux-create -t project -s 
```

## Formating sdcard
perhatikan bahwa sdcard saya termounting di ```/dev/sda```

```bash
sudo fdisk /dev/sda
```
create app
```bash
petalinux-create -t apps --template c --name myapp1 --enable
```

```bash
petalinux-package --boot --fsbl zynq_fsbl.elf --u-boot --fpga system.bit
```

# petalinux config

[gpio](https://www.linkedin.com/pulse/gpio-petalinux-part-3-go-uio-roy-messinger/)

# Notes
2 hari yang lalu saya berhasil membuat bootloader hingga sampai loading rootfs namun setelah package bootimage yang sekarang justru 
```boot.bin``` mengalami error di das-u-boot

saya mengganti nilai DTG pada config command dengan nilai [zc702](https://support.xilinx.com/s/question/0D52E00006iHj5KSAS/is-is-possible-to-update-configurations-after-creating-project-with-bsp-?language=en_US)