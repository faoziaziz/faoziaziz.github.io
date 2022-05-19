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




### Referensi

1. [Hackster Zynq Petalinux](https://www.hackster.io/news/an-fpga-take-on-the-raspberry-pi-petalinux-on-the-zynqberry-67dd421d25aa?fbclid=IwAR1l1ZmnCwhxk3aGbeGyPZGBNChTaLKoGMYXj52ur3QeTc3I8IaV4ZRwI6g)
