---
layout: post
title: "Install Cake PHP"
date: 2018-11-12 19:15:40 +0700
comments: true
categories: [cake, php]
---
Untuk membuat sebuah struktur frameworkd dari cakers kita harus menginstall
composer dahulu, karena saya asumsikan anda telah menginstall cakers kali ini
langsung generate kode buat di develop.

```bash
composer create-project --prefer-dist cakephp/app cakers
```

lalu jalanakan code yang didevelop tadi dengan menggunakan perintah berikut

```bash
cd cakers
./bin/cake server
```
setelah itu akan muncul tulisan localhost dan port yang harus anda akses dengan
menggunakan web browser lalu akseslah dengan webbrowser alamat ip dan portnya.
biasanya localhost:8765
