---
title: 'Meca Sport'
date: 2017-12-13T01:11:52+00:00
author: winardiaris
layout: post
permalink: /meca-sport/
image: https://github.com/winardiaris/blog/raw/master/images/meca-sport.jpg
categories:
  - Catatan
  - Catetan
  - Linux
---

![Meca Sport](https://github.com/winardiaris/blog/raw/master/images/meca-sport.jpg "Meca Sport")  
Jajan bulan ini banyak banget, pelampiasan bulan-bulan kemarin. Salah satu jajanannya adalah Digital Alliance Meca Sport 60%.

Harga murah dan ukuran papan tik 60% yang menjadi patokan saya untuk membeli papan tik mekanik. 
Ada lampu LED nya tapi bukan RGB hanya warna biru, tak apa memang saya kurang suka dengan kelap-kelip si RGB. 

Karena ukurannya hanya 60% banyak tombol-tombol yang hilang salah satunya tombol arah, bukan hilang sepenuhnya tapi dikombinasikan dengan tombol Fn + WASD. Ini yang membuat saya perlu beradaptasi lagi.

Tombol lain yang dipadatkan/digabung ialah tombol fungsi (F1-F12) yang digabung dengan tombol angka (1-0). Eit, ternyata tombol ini tidak berfungsi dengan baik di Distro Linux (Ubuntu, openSUSE). Tombol yang keluaran (output) tidak  sama dengan tombol masukan (input).  
![Keycode](https://github.com/winardiaris/blog/raw/master/images/keycode.png "Keycode")

Untuk memperbaikinya saya pakai perintah-perintah berikut

```bash
rm -rf ~/.Xmodmap 

xmodmap -e "keycode 232 = F1"
xmodmap -e "keycode 233 = F2"
xmodmap -e "keycode 128 = F3"
xmodmap -e "keycode 212 = F4"
xmodmap -e "keycode 237 = F5"
xmodmap -e "keycode 238 = F6"
xmodmap -e "keycode 173 = F7"
xmodmap -e "keycode 172 = F8"
xmodmap -e "keycode 171 = F9"
xmodmap -e "keycode 121 = F10"
xmodmap -e "keycode 122 = F11"
xmodmap -e "keycode 123 = F12"

xmodmap -pke >~/.Xmodmap
sudo reboot

```


Salam.