---
layout: post
title: "Rust Embedded"
tags:
 - Diary
background: '/img/bg-about.jpg'
---
Memulai pembelajaran dengan rust menjadi menarik ketika sekarang kernel ternyata bisa dibuild dengan menggunakan rust. Saya mencari beberapa tutorial menggunakan rust dan qemu.

Saya menggunakan MSYS UCRT64 sebagai awal test agar nantinya program bisa dilakukan langsung dirun dengan menggunakan qemu.

pertama install cargo generate
```bash
cargo install cargo-generate
```
kemudian generate beberapa project.
```bash
cargo generate --git https://github.com/rust-embedded/cortex-m-quickstart

```

dalam code src nanti kalian akan menemukan code seperti berikut

```rust 
#![no_std]
#![no_main]

// pick a panicking behavior
use panic_halt as _; // you can put a breakpoint on `rust_begin_unwind` to catch panics
// use panic_abort as _; // requires nightly
// use panic_itm as _; // logs messages over ITM; requires ITM support
// use panic_semihosting as _; // logs messages to the host stderr; requires a debugger

use cortex_m::asm;
use cortex_m_rt::entry;

#[entry]
fn main() -> ! {
    asm::nop(); // To not have main optimize to abort in release mode, remove when you add code

    loop {
        // your code goes here
    }
}

```
ternyata ketika saya membuildnya dengan command 
```bash 
cargo build --target thumbv7m-none-eabi
```
memberikan error bahwa 
```bash
error: failed to download `proc-macro2 v1.0.70`
```
saya mencoba check versionnya ternyata versi ke 
```bash
$ rustc --version
rustc 1.42.0 (b8cedc004 2020-03-09)
```
lalu saya update dengan perintah 
```bash
rustup update
```
walaupun ada notivikasi telah terupdate ke versi 
1.72.0 tetapi tetap saja ahsil rustc --version
masih sama seperti berikut
```bash
>rustc --version
rustc 1.42.0 (b8cedc004 2020-03-09)
```
akhirnya saya memilih untuk menguninstall rust tersebut dengan command berikut.
```bash 
rustup self uninstall
```
kemudian saya install lagi dengan rust init yang saya download pada pc windows saya, dan ternyata berhasil. Saya coba lagi membuild ulang dengan 

```bash
cargo install cargo-generate
```
1. [Rust Embedded](https://docs.rust-embedded.org/book/start/qemu.html)