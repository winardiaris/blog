---
title: 'Memasang Firefox Quantum di openSUSE Tumbleweed'
date: 2017-10-10T23:11:52+00:00
author: winardiaris
layout: post
permalink: /memasang-firefox-quantum-di-opensuse-tumbleweed/
image: https://github.com/winardiaris/blog/raw/master/images/firefox-quantum-web.png
categories:
  - Catatan
  - Catetan
  - openSUSE
---

Kunjungi halaman [https://www.mozilla.org/id/firefox/channel/desktop/#beta](https://www.mozilla.org/id/firefox/channel/desktop/#beta) klik tombol unduh Firefox Beta

![Unduh](https://github.com/winardiaris/blog/raw/master/images/firefox-beta-download.png "Unduh")

Ekstrak hasil unduhan dengan cara:
```bash
cd /ke/tempat/unduhan/berada/
tar xjf firefox-57.0b5.tar.bz2
cd firefox 
ls
```

Untuk menjalankannya
```bash
./firefox
```


agar mudah untuk menjalankan via menu kita buat berkas *.desktop pada direktori `~/.local/share/applications` 

```bash
vim ~/.local/share/applications/firefox-beta.desktop

```
salin tempel kode dibawah
```
[Desktop Entry]
Categories=Network;WebBrowser;GTK;
Encoding=UTF-8
Name=Firefox Beta
GenericName=Web Browser
Comment=Web Browser
TryExec=/ke/tempat/ekstrak/berada/firefox
Exec=/ke/tempat/ekstrak/berada/firefox %u
Icon=/ke/tempat/ekstrak/berada/browser/icons/mozicon128.png
Terminal=false
StartupNotify=true
MimeType=text/html;text/xml;application/xhtml+xml;application/vnd.mozilla.xul+xml;text/mml;application/x-xpinstall;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
Type=Application

Actions=PrivateBrowsing;

[Desktop Action PrivateBrowsing]
Name=New Private Browsing Window
Exec=/ke/tempat/ekstrak/berada/firefox --private-window %u

```



Salam.