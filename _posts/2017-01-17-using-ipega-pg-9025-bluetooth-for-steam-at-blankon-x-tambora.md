---
id: 315
title: Using IPEGA PG-9025 Bluetooth for Steam at BlankOn X Tambora
date: 2017-01-17T23:47:38+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=315
permalink: /using-ipega-pg-9025-bluetooth-for-steam-at-blankon-x-tambora/
dsq_thread_id:
  - "5470469559"
image: /wp-content/uploads/2017/01/photo_2017-01-17_23-42-46.jpg
categories:
  - BlankOn
  - Catatan
  - Catetan
  - Steam
  - Tutorial
tags:
  - "9025"
  - BlankOn
  - game
  - ipega
  - steam
---
Saya memilki Joystick IPEGA ini karena bergabung dengan Pengembang BlankOn. 😀

Langsung saja.

1. Pasang paket berikut:
```bash
  sudo apt install -y xboxdrv
```
2. Hubungkan Ipega dengan dengan komputer/laptop anda, caranya tekan tombol X + Home sampai lampu led berkedip.
3. Buka pengaturan bluetooth dan cocokan [<img class="aligncenter size-full wp-image-316" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png?resize=700%2C394" alt="" srcset="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png?w=1366 1366w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png?resize=300%2C169 300w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png?resize=768%2C432 768w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png?resize=1024%2C576 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />](https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-07.png) [<img class="alignnone size-full wp-image-317" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png?resize=700%2C394" alt="" srcset="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png?w=1366 1366w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png?resize=300%2C169 300w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png?resize=768%2C432 768w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png?resize=1024%2C576 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />](https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-09-22.png)

4. Setelah Ipega terhubung cari Nomor _device_ **( /dev/input/eventXX )** dengan cara
```bash
cat /proc/bus/input/devices
```
akan tampil seperti ini [<img class="aligncenter size-full wp-image-318" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png?resize=700%2C325" alt="" srcset="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png?w=1028 1028w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png?resize=300%2C139 300w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png?resize=768%2C357 768w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png?resize=1024%2C476 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-15-06.png)</li>

5. Ubah pengaturan **vboxdrv** agar sesuai dengan ipega dengan cara berikut :
```bash
sudo xboxdrv --evdev /dev/input/eventXX --evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_Z=x2,ABS_RZ=y2,ABS_HAT0X=dpad_x,ABS_HAT0Y=dpad_y --axismap -Y1=Y1,-Y2=Y2 --evdev-keymap BTN_A=a,BTN_B=b,BTN_X=x,BTN_Y=y,BTN_TL=lb,BTN_TR=rb,BTN_TL2=lt,BTN_TR2=rt,BTN_THUMBL=tl,BTN_THUMBR=tr,BTN_SELECT=back,BTN_START=start --silent &
```
jangan lupa ubah **/dev/input/eventXX** sesuai pada poin ke empat</li>

5. Buka _Steam big picture mode_ [<img class="aligncenter size-full wp-image-321" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png?resize=700%2C381" alt="" srcset="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png?w=1366 1366w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png?resize=300%2C163 300w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png?resize=768%2C418 768w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png?resize=1024%2C558 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-32-51.png) [<img class="aligncenter size-full wp-image-322" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png?resize=700%2C394" alt="" srcset="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png?w=1366 1366w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png?resize=300%2C169 300w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png?resize=768%2C432 768w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png?resize=1024%2C576 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2017/01/Screenshot-from-2017-01-17-23-34-11.png)

ada tahap ini Ipega telah dapat digunakan.</ol>


Jika ada pertanyaan silakan berkomentar dibawah. 😀

Selamat mencoba.

&nbsp;

Sumber :

* https://steamcommunity.com/app/221410/discussions/0/558748653738497361/
* https://drive.google.com/file/d/0B2SVXPgdVdQ1SEkxR2hYOU1iVW8/view