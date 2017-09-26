---
id: 45
title: Konversi Video dari mov ke mp4 secara masal menggunakan ffmpeg
date: 2016-05-11T12:33:59+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=45
permalink: /konversi-video-dari-mov-ke-mp4-secara-masal-menggunakan-ffmpeg/
dsq_thread_id:
  - "4816894903"
image: /wp-content/uploads/2016/05/mov-to-mp4.png
categories:
  - Catetan
tags:
  - convert
  - ffmpeg
  - mov
  - mp4
  - video
---
Beberapa saat lalu saya diberi file video rekaman destop pelatihan oleh salah satu dosen pemrograman saya di Universitas Pancasila. Tidak sedikit file yang dikasih sekitar 36Gb kebanyakan berektensi .mov dan ada beberapa file yang besarnya >1Gb.

Yang menjadi masalah adalah ruang kosong pada hardis saya penuh dibuatnya, maka daripada itu saya akan menkonversi dan menkompres file tersebut.

berikut cara yang saya lakukan<!--more-->

<pre class="brush: bash; title: ; notranslate" title="">$ cd folder/berkas/
$ for f in $(find . -type f -name "*.mov"); do ffmpeg -i "$f" -codec copy -vcodec libx264 -crf 20 "${f%.avi}.mp4"; done
</pre>

**sepotong keluaran dari perintah diatas**

<pre class="brush: bash; title: ; notranslate" title="">ffmpeg version 2.8.6-1ubuntu2 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-11ubuntu1) 20160311
  configuration: --prefix=/usr --extra-version=1ubuntu2 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from './training_android/Hari_2/03._Menggunakan_Database_SQLite.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2016-04-12 04:28:02
  Duration: 00:43:57.32, start: 0.000000, bitrate: 3090 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p(tv, bt709), 1366x768 [SAR 1:1 DAR 683:384], 2824 kb/s, 59.68 fps, 60 tbr, 6k tbn, 50 tbc (default)
    Metadata:
      creation_time   : 2016-04-12 04:28:02
      handler_name    : Core Media Data Handler
      encoder         : H.264
    Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 257 kb/s (default)
    Metadata:
      creation_time   : 2016-04-12 04:28:02
      handler_name    : Core Media Data Handler
[libx264 @ 0x238f380] using SAR=1/1
[libx264 @ 0x238f380] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x238f380] profile High, level 4.2
[libx264 @ 0x238f380] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=20.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[mp4 @ 0x24f8d60] Codec for stream 1 does not use global headers but container format requires global headers
Output #0, mp4, to './training_android/Hari_2/03._Menggunakan_Database_SQLite.mov.mp4':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    encoder         : Lavf56.40.101
    Stream #0:0(und): Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv420p, 1366x768 [SAR 1:1 DAR 683:384], q=-1--1, 60 fps, 15360 tbn, 60 tbc (default)
    Metadata:
      creation_time   : 2016-04-12 04:28:02
      handler_name    : Core Media Data Handler
      encoder         : Lavc56.60.100 libx264
    Stream #0:1(und): Audio: aac ([64][0][0][0] / 0x0040), 44100 Hz, stereo, 257 kb/s (default)
    Metadata:
      creation_time   : 2016-04-12 04:28:02
      handler_name    : Core Media Data Handler
Stream mapping:
  Stream #0:0 -&gt; #0:0 (h264 (native) -&gt; h264 (libx264))
  Stream #0:1 -&gt; #0:1 (copy)
Press [q] to stop, [?] for help
[mp4 @ 0x24f8d60] Packet with invalid duration -2960 in stream 1rate= 722.5kbits/s dup=833 drop=0    
frame=158239 fps= 76 q=-1.0 Lsize=  236909kB time=00:43:57.36 bitrate= 735.9kbits/s dup=833 drop=0    
video:149759kB audio:82930kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.813857%
[libx264 @ 0x238f380] frame I:696   Avg QP:16.44  size:136910
[libx264 @ 0x238f380] frame P:42098 Avg QP:20.09  size:  1095
[libx264 @ 0x238f380] frame B:115445 Avg QP:28.67  size:   104
[libx264 @ 0x238f380] consecutive B-frames:  2.3%  1.0%  0.6% 96.1%
[libx264 @ 0x238f380] mb I  I16..4: 33.9% 24.7% 41.4%
[libx264 @ 0x238f380] mb P  I16..4:  0.6%  0.3%  0.3%  P16..4:  0.9%  0.1%  0.1%  0.0%  0.0%    skip:97.8%
[libx264 @ 0x238f380] mb B  I16..4:  0.0%  0.1%  0.0%  B16..8:  0.8%  0.0%  0.0%  direct: 0.0%  skip:99.0%  L0:50.0% L1:49.8% BI: 0.3%
[libx264 @ 0x238f380] 8x8 transform intra:32.1% inter:29.2%
[libx264 @ 0x238f380] coded y,uvDC,uvAC intra: 22.2% 16.4% 14.6% inter: 0.1% 0.1% 0.1%
[libx264 @ 0x238f380] i16 v,h,dc,p: 53% 47%  0%  0%
[libx264 @ 0x238f380] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 39% 11% 49%  0%  0%  0%  0%  0%  0%
[libx264 @ 0x238f380] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 35% 34% 11%  2%  3%  4%  4%  3%  4%
[libx264 @ 0x238f380] i8c dc,h,v,p: 79% 15%  6%  1%
[libx264 @ 0x238f380] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0x238f380] ref P L0: 71.2%  3.8% 17.2%  7.7%
[libx264 @ 0x238f380] ref B L0: 65.1% 33.0%  1.9%
[libx264 @ 0x238f380] ref B L1: 95.2%  4.8%
[libx264 @ 0x238f380] kb/s:465.18
</pre>

Dari 6 pagi tadi hingga saat saya mencatat ini proses konversi belum selesai. dan inilah tangkap layar prosesor yang sedang bekerja <img class="alignnone size-full wp-image-51" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-11-12-30-25.png?resize=700%2C394" alt="Screenshot from 2016-05-11 12-30-25" srcset="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-11-12-30-25.png?w=1366 1366w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-11-12-30-25.png?resize=300%2C169 300w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-11-12-30-25.png?resize=768%2C432 768w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/05/Screenshot-from-2016-05-11-12-30-25.png?resize=1024%2C576 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />

_Selamat Mencoba_

&nbsp;

_ilustrasi mov->mp4 gambar dari http://www.apowersoft.com/_