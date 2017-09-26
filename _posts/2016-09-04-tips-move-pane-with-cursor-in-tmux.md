---
id: 86
title: '[Tips] Move pane with cursor in Tmux'
date: 2016-09-04T21:49:48+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=86
permalink: /tips-move-pane-with-cursor-in-tmux/
dsq_thread_id:
  - "5118686052"
image: /wp-content/uploads/2016/09/tmux.png
categories:
  - Catetan
tags:
  - catetan
  - terminal
  - tips
  - tmux
---
Awalnya saya sering menggunakan pintasan papan ketik untuk memindahkan jendela pada tmux. hal ini sangat merepotkan bila dilakukan dengan sering. Berikut konfigurasi yang saya temukan setelah berselancar di google.<!--more-->

Buat berkas

<pre class="brush: bash; title: ; notranslate" title="">~/.tmux.conf </pre>

dan salin konfigurasi ini.

<pre class="brush: bash; title: ; notranslate" title="">set-option -g -q mouse on
bind m \
  set-option -g -q mouse on
  
bind M \
  set-option -g -q mouse off

</pre>

Selamat mencoba.