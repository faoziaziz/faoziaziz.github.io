---
layout: post
title: "React vs Vue ep 1"
date: 2018-12-05 19:00:24 +0700
comments: true
categories: [React, Vue]
---
# Install Vue

Untuk menjawab permintaan penggemar (wkkwkwk) tentang perbandingan vue dengan
react, kali ini saya akan mencoba vuejs dahulu, karena pengalaman saya hanya
sekedar angular dan react, jadi kalo bikin perbandingan antara vue vs react nanti
jadinya kurang credible.

untuk install vue gunakan perintah berikut

```sh
sudo npm install -g vue
sudo npm install -g vue-cli
```
lalu inisiasi kodenya dengan perintah berikut ini

```sh
vue init webpack faoziaziz-vue
```
itu pake webpack dulu yah karena kalau mau pake semisal appolo buat develop native
masih cupu saya.

lalu pilih perintah seperti berikut

```sh
? Project name faoziaziz-vue
? Project description Ini mau di deploy pake heroku
? Author Aziz Amerul Faozi <admin@labseni.com>
? Vue build standalone
? Install vue-router? Yes
? Use ESLint to lint your code? No
? Set up unit tests No
? Setup e2e tests with Nightwatch? No
? Should we run `npm install` for you after the project has been created? (recomme
nded) npm

```

lalu masuk ke direktory vue-nya sekalian run

```sh
cd faoziaziz-vue
vue run dev
```

kemudian cek di localhost:8080, karena saya deploy di heroku bisa di cek di
[faoziaziz heroku](https://faoziaziz.herokuapp.com), dan ternyata error.

jadi saya tambahin file Procfile dengan isi sebagai berikut

```sh
web: npm run dev
```
dan ternyata tetep eror jadi, saya buat backend dengan express, jadi saya menambahkan
dengan perintah berikut

```sh
npm install --save express
```
dan membuat file server.js dengan isi seperti berikut

```js

var express = require('express');
var path = require('path');
var serveStatic = require('serve-static');

app = express();
app.use(serveStatic(__dirname + "/dist"));

var port = process.env.PORT || 5000;
app.listen(port);

console.log('server started '+ port);
```

lalu merubah package.json bagian startnya dengan code berikut dan mendelete file
Procfile-nya

```json
"scripts": {
  "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
  "start": "node server.js",
  "build": "node build/build.js"
},
```

build kodenya seperti berikut
```sh
npm run build
```
lalu push lagi ke heroku. ternyata eror lagi

kemudian saya mendelete kode /dist/ dalam .gitignore,

dan akhirnya jalan [faoziaziz-vue](https://faoziaziz.herokuapp.com).

# Perbandingan Vue vs React

# Kesamaan
Dari situ keduanya bergerak di ranah library frontend karena vue membutuhkan
expressjs untuk backendnya agar bisa dipasang ke heroku.

# Perbedaan
Untuk pemasangan di heroku, react tidak membutuhkan tambahan, dia push langsung jalan.
Tidak seperti vue yang harus nambah settingan lagi. Sayangnya sewaktu saya menggunakan
react, dia susah dikombinasikan dengan express js, jadi dengan vue js, akan lebih enak
kombinasi dengan backend seperti express. Saya pernah mengkombinasikan antara react
dengan Spring (framworknya jawa buat web) dan ternyata membutuhkan port yang lebih banyak
selain itu kombinasinya lebih nyebelin dengan menggunakan methode fetching json.
