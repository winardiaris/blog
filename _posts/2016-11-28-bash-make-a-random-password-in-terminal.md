---
id: 284
title: '[bash] Make a random password in terminal'
date: 2016-11-28T21:26:48+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=284
permalink: /bash-make-a-random-password-in-terminal/
dsq_thread_id:
  - "5338285576"
categories:
  - Bash
  - Catatan
  - Catetan
tags:
  - bash
  - linux
  - password
---
Tulisan ini sebagai pengingat diri untuk membuat password yang kuat dengan mengandalkan perintah yang ada di bash. Mungkin bisa menambah pengalaman bagi anda.

Berikut caranya :

1. Menggukanan kombinasi perintah `echo` , `md5sum` dan `base64`
  ```bash
  $ echo "ini text password saya" | md5sum | base64 | head -c10 ; echo
  ```
  pada tulisan `ini text password saya`, bisa diubah menjadi kata/kalimat yang mudah diingat oleh anda dan pada `-c10` bisa diubah panjang _password_ nya sesuai keinginan anda

2. Menggunakan fitur `/dev/urandom`
```bash
$ < /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c10 ;echo; tr -cd '[:alnum:]' &lt; /dev/urandom | fold -w30 | head -n1
```
- pada `-c10` bisa diubah panjang _password_ nya sesuai keinginan anda
- pada `-w30` bisa diubah panjang _password_ nya sesuai keinginan anda
cara lain menggunakan `/dev/urandom`
```bash
$ strings /dev/urandom | grep -o '[[:alnum:]]' | head -n 30 | tr -d '\n'; echo
```
bisa juga yang _simple_ seperti ini
```bash
$ < /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c6
```
3. Yang ini menggunakan fungsi rand pada openssl. yang mungkin tidak terpasang secara bawaan pada sistem operasi anda
```bash
$ openssl rand -base64 32
```
4. Menggunakan `pwgen`
```bash
$ sudo apt-get install pwgen
$ pwgen
Aica0yei chaeW1ja shoh9uoB ta4phaiZ iePa0ooc etapeeL1 wae4Iung baiH5sai
timou1Ph ohw2Ahxu aiW1ohfe iemae9Th Vuf1iu7a eipu9ooM ieth1ohR hew9aePh
yoc2Quee ze7Pei4o Iloo7aeg MooNg5ph Vus4phia gi3uQu3f ue4Aibai Yeinga0i
aitooSh3 DooSePh4 see9Eiyi OhNg2che XeeX6iGi chei5Lei aecieFe3 egh8gaiZ
QuoRaiz0 Zeejai8A Zefoogh8 boYae6ag aeka7eTh tie3daiD aSei4oe1 pae8Aeke
Ichahd6o ChaiB2oh Coeth3ai coTho5qu vaKa6she eveeZah3 Rea0ogoo aht3ueXo
uuVaph0p zaeY1phi gieFo3ph Uphaiwe0 quoo9ieK sheeR0ae Cae2oihe aiFeiZ0g
faiFae9u Eewoh0pe Mai3eere fauWee4i ieluL7ae Mohxah6o Ujeev8oo Eiv6ees0
ieB0aix9 go6it9Pa eiWee9ew eesai4Ei lieN9Ni9 Eic0ooya theuMah8 bie7Wedu
eikai5Ue Jai3deep aiN9Da1i weer2fuT NahSh9ph lioteeL8 ahFa4eud teeh9uuY
Aegher5u Isheib9E iGhee8ca aSha0Kae kaePh9Xo Een6ieNg iMeegh8a ohChiiw4
da9iJah2 Eim9naeh gohl8Wah liePes3n ahThooL0 Ei5aejiv Su0madah aeph8Fie
Eezujei1 Meca7tha Rahj3tee In8coh6x eiCh0ooc yuLai4oh Aid6eig1 buShooV0
meaTahR4 Aewo0aa6 xaeS5xei joo9yuMo taiJoh4a Ogh0uefo ouZ9wae0 ohT4EoGh
jieYu2ai oQu5Rai2 douNi9yu mohie1Zu iePhee8h aibohS8f Dei7shee Eec0cood
oY4buive Ooquaju2 Aevo5rai duvi0Tui daixaeT8 Ong6uuSh aeShahk5 Aibahth3
ceiLuoz3 nohS9kei Ieph4loh Iemeux5S Cheuf2ee Vieg8ipu quugei3K nau4Chu8
JeeXie5u fel9Uo1z ooMozuo2 joh1Lae2 Eib8KohX daeyo4Ti Wee1he9S eefe6WaX
Tiulei6u Phieboh1 duaHae4o eiFag9io ooZe9eix aesh3Jie ooca5ieB iYooxah2
Noofo6sh eiph8Ech oequ8Oj7 phijaeC4 boh9Ohhi aip9ooNa ei8Eiy1l gahbei3P
```
5. Menggunakan `makepasswd`
```bash
$ sudo apt-get install makepasswd
$ makepasswd --count 5 --chars 32
FMPp05phTpVrm80Cexa0Jv1UDvXwU5Sr
UD8J8EL7UgUCCmIjL6IqGN2ImnGebDjR
aRGnbhfdIi5YAwqnb1nnAJ4x1C3b48PL
orreMBDCv5EVVP0cU4ndDQr1q0dnJGjD
0WG12JpH0aijg88T4NbiT86z7J3X2URE
```

Itulah beberapa cara yang bisa digunakan untuk membuat password.

**Selamat hari Senin**