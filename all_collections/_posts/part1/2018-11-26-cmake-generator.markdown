---
layout: post
title: "cmake generator"
date: 2018-11-26 18:52:06 +0700
comments: true
categories:
---
Kali ini saya mencoba untuk membuat generator seperti maven nya java atau nodenya
milik java script untuk itu pertama kita harus menginstall cmake terlebih dahulu

```bash
sudo dnf install -y cmake
```
setelah itu buat direktory untuk digenerasi sebagai struktur dari cmake semisal
AlegroCpp

```bash
mkdir AlegroCpp
cd AlegroCpp
```
lalu buat file CMakeLists.txt yang berisi kode berikut ini

```text
cmake_minimum_required (VERSION 2.6)
project (Tutorial)
# The version number.
set (Tutorial_VERSION_MAJOR 1)
set (Tutorial_VERSION_MINOR 0)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")

# add the executable
add_executable(Tutorial tutorial.cxx)

```
file diatas merupakan konfigurasi cmakenya. Lalu buat file tutorial.cxx dalam
folder berikut dengan isi berikut

```cpp
/*
  filename : tutorial.cxx
*/
// A simple program that computes the square root of a number
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "TutorialConfig.h"

int main (int argc, char *argv[])
{
  if (argc < 2)
    {
    fprintf(stdout,"%s Version %d.%d\n",
            argv[0],
            Tutorial_VERSION_MAJOR,
            Tutorial_VERSION_MINOR);
    fprintf(stdout,"Usage: %s number\n",argv[0]);
    return 1;
    }
  double inputValue = atof(argv[1]);
  double outputValue = sqrt(inputValue);
  fprintf(stdout,"The square root of %g is %g\n",
          inputValue, outputValue);
  return 0;
}

```

setelah itu buat file TutorialConfig.h.in dengan isi berikut ini
```cpp
// the configured options and settings for Tutorial
#define Tutorial_VERSION_MAJOR @Tutorial_VERSION_MAJOR@
#define Tutorial_VERSION_MINOR @Tutorial_VERSION_MINOR@
```

kemudian generate cmakenya dengan perintah berikut
```bash
cmake .
```
kemudian build dan run
```bash
make
./Tutorial 4
```
