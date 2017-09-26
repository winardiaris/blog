---
id: 75
title: '[bash] Mencari kata dalam file secara rekursif'
date: 2016-08-09T19:11:43+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=75
permalink: /bash-mencari-kata-dalam-file-secara-rekursif/
dsq_thread_id:
  - "5052070997"
categories:
  - Bash
  - Catetan
tags:
  - bash
  - catetan
  - linux
---
Kadang saat kita telah mengetik banyak file dan ratusan baris, kita lupa kata tertentu terdapat di file mana saja.

Dengan menggunakan perintah **grep** kita dapat mencari suatu kata / kalimat pada file secara rekursif.

<pre class="brush: bash; title: ; notranslate" title="">$ cd folder/kerja/anda
$ grep -rnw . -e "text yang dicari"
</pre>

<!--more-->Untuk memudahkan dalam penggunaan yang sering, kita buatkan berkas di folder 

**~/.local/bin/**

<pre class="brush: bash; title: ; notranslate" title="">$ vi ~/.local/bin/cari
</pre>

<pre class="brush: bash; title: ; notranslate" title="">#!/bin/bash
export t="$1"

pwd=$('pwd')
echo "=================================="
echo "$pwd"
echo "Text yang dicari [$t]"
echo "=================================="

grep -rnw . -e "$t"
</pre>

Jangan lupa untuk memberi akses execute pada berkas tadi.

<pre class="brush: bash; title: ; notranslate" title="">$ chmod +x ~/.local/bin/cari
</pre>

selanjutnya untuk mencari kata/kalimat yang akan anda cari hanya mengetikan perintah:

<pre class="brush: bash; title: ; notranslate" title="">$ cari [kata]
$ cari "[kata yang dicari]"
</pre>

*** ingat di unix-like itu** _<a href="https://en.wikipedia.org/wiki/Case_sensitivity" target="_blank">case-sensitive</a>_