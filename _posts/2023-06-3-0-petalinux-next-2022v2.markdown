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

saya mengganti nilai DTG pada config command dengan nilai [zc702](https://support.xilinx.com/s/question/0D52E00006iHj5KSAS/is-is-possible-to-update-configurations-after-creating-project-with-bsp-?language=en_US)