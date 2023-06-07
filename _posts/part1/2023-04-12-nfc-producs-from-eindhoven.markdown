---
layout: post
title: "NFC producs from Eindhoven"
tags:
 - Embedded
---
What we need to make some NFC producs? The first You need to develop NFC producs, then You need add microcontoller to controll the NFC, connected via SPI. I will use NUCLEO-F446RE then i will program it.

The Algorithm
1. We need to set CS to be LOW
2. We will try to send HAL_SPI_Transmit
3. We will Try to receive data with HAL_SPI_Receive
4. Decativeate to set CS to be high. 