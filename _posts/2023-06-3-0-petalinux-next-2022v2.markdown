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
