---
title: "Install Driver QPOS Q58M on Raspbian"
date: 2019-05-04T10:10:00+00:00
author: winardiaris
layout: post
permalink: /q58m-raspbian/
image: https://ecs7.tokopedia.net/img/cache/700/product-1/2016/9/22/12258882/12258882_b7fd6ea8-74cb-4738-b8a5-361f03569f17.jpg
categories:
  - Catatan
  - Catetan
  - Linux
  - Debian
  - Raspi
  - Printer
tags:
  - printer
  - debian
  - raspi
  - linux
  - pos
---

![QPOS Q58M](https://ecs7.tokopedia.net/img/cache/700/product-1/2016/9/22/12258882/12258882_b7fd6ea8-74cb-4738-b8a5-361f03569f17.jpg "QPOS Q58M")

# Tulisan ini untuk pengingat diri

Pada aplikasi POS biasanya membutuhkan _thermal printer_ untuk mencetak struk.

Pada kasus ini aplikasi POS yang digunakan **SiKOKO** _Web base application_ dengan Printer QPOS Q58M, agar printer bekerja kita mebutuhkan driver untuk printer tersebut.

Kebetulan printer QPOS Q58M ini bisa menggunakan driver milik Zijiang Zj-58.

Berikut cara memasang drivernya:

## 1. Memasang _dependencies_

```bash
sudo apt update
sudo apt install -y build-essential cmake libcups2-dev libcupsimage2-dev git build-essential cups system-config-printer
```

## 2. Unduh driver

```bash
cd ~/Downloads
git clone https://github.com/klirichek/zj-58.git
```

## 3. Memasang driver

```bash
cd zj-58
mkdir build && cd build && cmake ../
cmake --build .
sudo make install
```

## 4. Menambahkan printer

- Menu > Preferences > Print Settings  
  ![Print Settings](https://github.com/winardiaris/blog/raw/master/images/print-settings.png "Print Settings")
- Klik tombol ADD dah masukan password sudo  
  ![Password](https://raw.githubusercontent.com/winardiaris/blog/master/images/printer-password.png "Password")
- Pada devices pilih Unknown (?) dan connection pilih USB
  ![Unknown](https://github.com/winardiaris/blog/raw/master/images/printer-unknown.png "Unknown")
- Choose Printer pilih Zijiang  
  ![Zijiang Devices](https://github.com/winardiaris/blog/raw/master/images/printer-zijiang.png "Zijiang Devices")
- Choose Driver pilih ZJ-58  
  ![ZJ58 Driver](https://github.com/winardiaris/blog/raw/master/images/printer-driver-zj58.png "ZJ58 Driver")
- Pada Installable Option tidak perlu di checklist  
  ![Installable Option](https://github.com/winardiaris/blog/raw/master/images/printer-options.png "Installable Option ")
- Pada Describe Printer ubah bagian:
  - Printer name: Q58M
  - Description: Q58M  
    ![Describe Printer](https://github.com/winardiaris/blog/raw/master/images/printer-desc1.png "Describe Printer")  
    ![Describe Printer](https://github.com/winardiaris/blog/raw/master/images/printer-desc2.png "Describe Printer")
- Masukan Password sudo  
  ![Password](https://github.com/winardiaris/blog/raw/master/images/printer-password2.png "Password")
- Klik Cancel pada print test  
  ![Print Test](https://github.com/winardiaris/blog/raw/master/images/printer-test.png "Print Test")

## 5. Mencoba Printer

Disini saya mencoba mencetak struk dari aplikasi SiKOKO. Jangan lupa untuk mengatur paper size sesuai kebutuhan dan margin menjadi minimal sebelum mencetak  
![Minimal Margin](https://github.com/winardiaris/blog/raw/master/images/printer-minimal-margin.png "Minimal Margin")  
_(contoh untuk Chrome/Chromium)_

---

### for terminal lazy

```bash
sudo apt update
sudo apt install -y build-essential cmake libcups2-dev libcupsimage2-dev git build-essential cups system-config-printer

cd ~/Downloads
git clone https://github.com/klirichek/zj-58.git

cd zj-58
mkdir build && cd build && cmake ../
cmake --build .
sudo make install
```

---

### Enable popup

**Chrome/Chromium**  
Buka **Settings** > **Content Settings** > **Popups** > **Allowed** (true)

**Firefox**  
Buka **Preferences** > **find/search (pop)** > **Block pop-up windows** > **disable**

---

### Packaging

```bash
sudo cpack -G DEB
```

---

Salam.  
`winardiaris`
