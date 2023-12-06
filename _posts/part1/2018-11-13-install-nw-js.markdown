---
layout: post
title: "Install NW js"
date: 2018-11-13 14:47:08 +0700
comments: true
categories:
---
Kali ini saya mencoba untuk membuat sebuah aplikasi desktop untuk nantinya akan digunakan dalam banyak hal seperti monitoring hardware atau untuk sekedar melakukan simulasi, kali ini saya mencoba untuk menggunakan framework dari nodejs seperti elektron dan NWjs untuk installasinya bisa dilakukan sebagai berikut

pastikan bahwa npm yang terinstall adalah npm yang latest dengan menggunakan perintah berikut

```bash
sudo npm install npm@latest --global
```


```bash
sudo npm install  -g nw
```
tapi biasanya mengalami error untuk itu cobalah masuk ke user root dan menginstallnya jika anda ingin sekali menginstallnya (karena tidak direkomendasikan meningstall dari bash root)

```bash
sudo su
npm install -g nw
```
jika tidak berhasil coba dengan perintah berikut ini
```bash
sudo su
sudo npm install -g --unsafe-perm=true --allow-root nw
```
Buat direktory untuk kerja kemudian inisiasi nwnya untuk bisa menggenerasi kode dalam strukur node.

```
mkdir allUI
cd allUI
npm init -y
```
rubah package.json codenya pada bagian main dari index.js menjadi index.html
dan bagian start ditambah kode "nw ." seperti berikut
```json
{
  "name": "allUI",
  "version": "1.0.0",
  "description": "",
  "main": "index.html",
  "scripts": {
    "start": "nw .",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
lalu pada terminal gunakan perintah berikut

```bash
npm start
```
tunggu nanti akan muncul gambar seperti berikut,

![AllUi](https://faoziaziz-heroku.s3.amazonaws.com/ALLui.png)

untuk ngoprek selanjutnya silahkan dengan kreatifitas sendiri.

untuk pengembangannya anda bisa mengikuti ngopreknya di [Desktop Serbaguna](https://github.com/faoziaziz/desktop-serbaguna)

kemudian install nw sdknya dengan perintah berikut

```bash
npm install nw@0.34.3-sdk --save-dev
```
