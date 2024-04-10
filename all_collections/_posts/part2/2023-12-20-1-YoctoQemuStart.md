---
layout: post
title: "Yocto Qemu Start"
tags:
 - Diary
background: '/img/bg-about.jpg'
---
Yocto adalah cara yang cukup enak untuk membangun sebuah operating system. Kali ini saya menggunakan yocto versi 4.0.4. Sebelum membuild project yocto pastikan beberapa hal terinstall. Saya menggunakan ubuntu versi 22.04

```bash
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool pylint
```
lalu clone code dari git yocto dengan branch kirkstone.

```bash
git clone https://git.yoctoproject.org/poky -b kirkstone
```
versi yang saya gunanakan adalah versi kirkstone. Hal ini dikarenakan saya menggunakan ubuntu versi 22.04. Kemudian masuk ke direktory pocky. lalu siapkan environment dengan mengeksekusi perintah berikut.

```bash
cd poky/
source oe-init-build-env build
```
kemudian build dengan perintah berikut

```bash
bitbake core-image-full-cmdline
```
jika terjadi error biasanya karena ketika build terjadi killed oleh machine karena process yang bertubrukan. Lakukan 
```bash
bitbake core-image-full-cmdline
```
lagi hingga tidak ada error karena killed. Jalankan perintah untuk menjalankan os yang dibentuk dengan perintah berikut. 
```bash
runqemu qemux86-64 core-image-full-cmdline
```

## Install toaster 

Toaster adalah framework dari django untuk membuild dengan menggunakan yocto. 
```bash
pip3 install --user -r bitbake/toaster-requirements.txt
```
lalu jalankan toaster dengan menggunakan perintah berikut.
```bash
cd poky
source oe-init-build-env
source toaster start
```
lalu check dengan browser pada alamat berikut
```bash
http://127.0.0.1:8000
```
jika anda ingin menggunakan port lain bisa menggunakan perintah berikut
```bash
source toaster start webport=8400
```


[Toaster Manual](https://docs.yoctoproject.org/4.0.14/toaster-manual/intro.html)