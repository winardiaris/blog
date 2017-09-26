---
id: 251
title: '[Catatan] Konversi berkas video dengan ffmpeg'
date: 2016-10-07T22:03:05+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=251
permalink: /catatan-konversi-berkas-video-dengan-ffmpeg/
dsq_thread_id:
  - "5205342853"
categories:
  - Catatan
  - Catetan
  - ffmpeg
tags:
  - convert
  - ffmpeg
  - video
---
2 Minggu terakhir ini ada pekerjaan membuat web untuk stream video.

Yang jadi masalah adalah berkas video yang diberikan oleh klien bermacam-macan ekstensi, ukuran resolusi, dan ukuran berkas. Maka dari itu saya konversi semua berkas video menjadi mp4 dengan resolusi 720p/480p dan format audio menjadi  mp3 dengan cara di bawah ini:<!--more-->

  * Menggabungkan berkas DVD <pre class="brush: bash; title: ; notranslate" title="">$ cat VTS_01_1.VOB VTS_01_2.VOB VTS_01_3.VOB &gt; JOIN.VOB
</pre>

  * Menkonversi format audio ke mp3 <pre class="brush: bash; title: ; notranslate" title="">$ ffmpeg -i FILENAME -acodec libmp3lame -ac 2 -ar 22050  output.mp4

</pre>

  * Menkonversi format audio ke mp3 dan mengubah ukuran menjadi 720p <pre class="brush: bash; title: ; notranslate" title="">$ ffmpeg -i FILENAME -acodec libmp3lame -ac 2 -ar 22050  -vf scale=-1:720 output_720.mp4

</pre>