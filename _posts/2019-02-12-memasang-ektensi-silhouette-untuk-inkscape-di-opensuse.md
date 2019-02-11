---
title: 'Memasang ekstensi silhouette untuk inkscape di openSUSE'
date: 2019-02-12T00:10:00+00:00
author: winardiaris
layout: post
permalink: /memasang-ektensi-silhouette-untuk-inkscape-di-opensuse/
image: https://www.silhcdn.com/2/i/p/s/i/silhouette-portrait-2-4t_01-xl.jpg
categories:
  - Catatan
  - Catetan
  - Linux
  - Debian
  - Silhouette
tags:
  - silhouette
  - potrait
  - extension
  - inkscape
  - opensuse
  - linux
  - cutting
  - machine
---

![Silhouette Potrait](https://www.silhcdn.com/2/i/p/s/i/silhouette-portrait-2-4t_01-xl.jpg "Silhouette Potrait")  

# Tulisan ini untuk pengingat diri

Akhir-akhir ini saya sedang tertarik pada _cutting machine_ dan kebetulan salah satu teman memilikinya.


Perangkat tersebut bermerk "**_Silhouette Potrait_**" yang membutuhkan aplikasi Silhouette Studio (https://www.silhouetteamerica.com/software) untuk mengoperasikannya yang notabennya berjalan pada sistem operasi Windows dan Mac OSX

Beberapa hari saya mencoba aplikasi tersebut namun tidak mudah memahaminya, karena saya  terbiasa dengan Inkscape. 

Selepas jam kerja saya berselancar mencari padanan aplikasi Silhouette Studio untuk distro openSUSE. Dan menemukan tautan https://github.com/fablabnbg/inkscape-silhouette sebuah ekstensi inkscape untuk mengoperasikan perangkat Silhouette. 


Berikut cara memasang extensi tersebut pada openSUSE:

- Buka Konsole/Terminal lalu ketik peritah dibawah ini

```bash
sudo zypper in python-usb
cd /tmp
git clone https://github.com/fablabnbg/inkscape-silhouette.git
cd inkscape-silhouette
sudo python2 setup.py build && sudo python2 setup.py install
sudo cp sendto_silhouette.* /usr/share/inkscape/extensions/
sudo cp -R silhouette /usr/share/inkscape/extensions/
```

- Buat berkas
```bash
sudo vi /etc/udev/rules.d/99-graphtec-silhouette.rules
```

- Lalu saltem kode berikut 
```bash
SUBSYSTEM=="usb", ATTR{idVendor}=="0b4d", ATTR{idProduct}=="1132", MODE="666"
```

- Simpan dah ketik perintah berikut
```bash
sudo udevadm trigger
```

- Jangan lupa tambahkan usergroup 'lp' ke akun anda
```bash
sudo useradd -g lp NAMAUSER
```

- Login dan logout dari sesi desktop


Hidupkan dan hubungkan perangkat pada komputer lalu buka aplikasi inkscape, buatlah gambar yang dinginkan dengan catatan berikut:

- Gambar harus dikonversi ke path
- Jika gambar terdiri dari beberapa objek gabungkan menjadi satu objek
- Gunakan satu warna untuk seluruh objek gambar

Setelah gambar siap di cetak klik **Extensions > Export > Send to Silhouette** dan tentukan jenis **Tools**, jenis **Media**, **Kecepatan** dan **Tekanan** sesuai kebutuhan anda. Klik **_Apply_** untuk mengirim ke perangkat silhouette.



Bonus 
template inkscape untuk alas bawaan dari Silhouette Potrait ukuran kertas A4 ([link](https://github.com/winardiaris/blog/raw/master/images/template.svg))




Salam.