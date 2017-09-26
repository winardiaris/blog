---
id: 54
title: Mengganti Alt+Klik Kiri Window Move
date: 2016-05-16T17:09:42+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=54
permalink: /mengganti-altklik-kiri-window-move/
dsq_thread_id:
  - "4838789305"
categories:
  - Catetan
  - Inkscape
tags:
  - catetan
  - inkscape
---
Pada beberapa _Desktop Environment_ tombol pintas Alt+Klik Kiri digunakan untuk menggeser jendela (_Window Move_) yang aktif. Ini akan menggangu anda pengguna aplikasi Inkscape untuk memlih objek yang berada di bawah objek lain.

Untuk mengganti tombol pintas Alt+Klik Kiri bisa dilakukan dengan 2 cara:<!--more-->

  1.  Menggunakan `dconf-editor` 
      * Install `dconf-editor` <pre class="brush: bash; title: ; notranslate" title="">$ sudo apt-get install dconf-tools</pre>
    
      * Buka `dconf-editor` <pre class="brush: bash; title: ; notranslate" title="">$ dconf-editor </pre>
    
      * Ubah pada `org` → `gnome` → `desktop` → `wm` → `preferences` → `mouse-button-modifier`→ Ubah sesuai keinginan anda <img class="alignnone size-full wp-image-55" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-16-17-04-31.png?resize=700%2C550" alt="Screenshot from 2016-05-16 17-04-31" srcset="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-16-17-04-31.png?w=800 800w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-16-17-04-31.png?resize=300%2C236 300w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-16-17-04-31.png?resize=768%2C603 768w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />
  2.  Menggunakan `gsettings` via terminal 
      * <pre class="brush: bash; title: ; notranslate" title="">$ gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier "&amp;amp;amp;lt;Super&amp;amp;amp;gt;"</pre>

#PEMBAHARUAN

Cara diatas tidak berlaku bila _desktop environment_ menggunakan **XFCE** dengan _window manager_ **XFWM.** Berikut cara mengganti Alt+Klik Kiri Window Move pada _desktop_ _environment_ **XFCE.**
  
Buka **xfce4-settings-editor.** Pada bilah sebelah kiri pilih **xfwm** dan pada kana pilih **easy_click.** Dan ubah sesuai keinginan anda

[<img class="size-full wp-image-312 aligncenter" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot_2017-01-03_00-14-11.png?resize=642%2C531" alt="" srcset="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot_2017-01-03_00-14-11.png?w=642 642w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot_2017-01-03_00-14-11.png?resize=300%2C248 300w" sizes="(max-width: 642px) 100vw, 642px" data-recalc-dims="1" />](https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot_2017-01-03_00-14-11.png)
  
Selamat Mencoba