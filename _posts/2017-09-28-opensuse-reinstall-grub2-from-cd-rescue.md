---
title: 'openSUSE re-install Grub2 from CD Rescue'
date: 2017-09-28T23:46:52+00:00
author: winardiaris
layout: post
permalink: /opensuse-reinstall-grub2-from-cd-rescue/
image: http://www.sisidunia.com/wp-content/uploads/2015/12/yuki.jpg
categories:
  - Catatan
  - Catetan
  - openSUSE
---
![Yuki Kato](http://www.sisidunia.com/wp-content/uploads/2015/12/yuki.jpg "Yuki Kato")

Ini bermula dari keisengan saya mencoba memasang Steam di openSUSE Tumbleweed di mesin yukikato (Thinkpad X220 dengan _hardisk_  lainnya). Kesana-kemari mencari cara dan tak kunjung berhasil. Akhirnya saya putuskan untuk menduakan openSUSE dengan Xubuntu.

Xubuntu + Steam berhasil terpasang. Namun, setelah saya nyalakan ulang mesin. Keresahan muncul karena openSUSE tidak ada dalam daftar grub. Masuklah ke Xubuntu untuk berselancar mencari cara mengembalikannya. Bertemulah saya dengan boot-repair, eh tetap saja openSUSE tidak masuk daftar grub.

Berselancar lagi ketemulah dengan [System Rescue CD](http://www.system-rescue-cd.org/Download/). Dibakarlah berkas citra __systemrescuecd-x86-5.1.0.iso__ ke _flashdrive_ dengan bantuan `dd`. Namun sayang tidak berhasil boot dengan baik.

Singkat cerita saya berkunjung ke forum openSUSE dan menemukan cara sbb:
1. Unduh berkas citra openSUSE Rescue CD dari tautan berikut: [http://download.opensuse.org/tumbleweed/iso/](http://download.opensuse.org/tumbleweed/iso/) dan bakar  ke _flashdrive_menggukan `dd`
2. CHROOT openSUSE  
    ```
    # mount /dev/sda1 /mnt
    # for i in proc sys dev; do mount --rbind /$i /mnt/$i ; done
    # chroot /mnt
    # mount -a
    ```
3. Pasang ulang grub
    ```
    # grub2-mkconfig -o /boot/grub2/grub.cfg
    # grub2-install /dev/sda
    # exit
    ```
4. Nyalakan ulang mesin  
    ```
    # reboot
    ```

Akhir kata  
Selamat malam,

Sumber:
```
https://www.suse.com/support/kb/doc/?id=7018126
https://forums.opensuse.org/content.php/128-Re-install-Grub2-from-DVD-Rescue
```

Photo:
```
http://www.sisidunia.com/wp-content/uploads/2015/12/yuki.jpg
```
