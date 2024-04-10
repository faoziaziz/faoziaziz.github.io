---
layout: post
title: "Review Assek Website"
date: 2018-11-18 09:36:57 +0700
comments: true
categories:
---

Website [Assekk](https://faoziaziz.herokuapp.com) akan direview kali ini, kali ini
saya mencoba untuk melatih menggunakan PERT (Program Evaluation Review Technique),
walaupun masih salah mungkin berusaha boleh-boleh saja lah yah wkwkwkk.

Saya masih tidak tahu apa itu teknik review dan evaluasi disini. Tapi mungkin maksudnya
review kelemahan dan kekurangan wkwkwkkw jadi mending bikin review asal yang tidak
menggunakan kaidah PERT dari pada tidak melakukannya sama sekali,

1. Bagian backend dari Website Assek tersebut tergolong cukup sustain, dengan menggunakan
fasilitas yang disediakan dari AWS seperti AWS DynamoDB, AWS S3 storage, serta AWS IoT core,
hal ini tidak membutuhkan maintenance yang alay untuk bisa mempertahankan server. AWS DynamoDB
gratis hingga pemakaian 25GB dan ini masih jauh dari kuoata segitu, dengan akses free tier
dana bisa ditekan, tapi apakah ini sampai lama (beberapa bulan lagi waktu free tier akan habis).

2. Dengan menggunakan Platform dari heroku, akses untuk frontend-nya bisa ditekan hingga nol rupiah,
tanpa harus menggunakan 3rd parti yang berlebihan dan bahkan sama sekali tidak menggunakan 3rd parti
ini memang menekan rupiah, karena tersambung dengan akses ke AWS, sayangnya bagian Dynos yang disediakan
heroku mau sampai kapan akan tetap lancar seperti itu, ini berlum diperhitungkan untuk koneksi yang besar.

3. NodeJS cukup bagus untuk mengembangkan banyak macam kebutuhan, seperti IoT, website, ataupun
backend yang lainnya. Tapi di website tersebut AWS IOT, DynamoDB, dan S3 Bucket tidak terintegrasi dengan
matang. Walau mereka disambungkan dalam satu website di heroku tapi ketiganya bahkan tidak memiliki relasi
sehingga hanya protokol yang berkerja secara terpisah. 
