---
id: 280
title: Rotate display with xrandr
date: 2016-11-20T01:08:49+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=280
permalink: /rotate-display-with-xrandr/
dsq_thread_id:
  - "5316902224"
categories:
  - BlankOn
  - Catatan
  - Catetan
tags:
  - display
  - linux
  - rotate
  - xrandr
---
Melihat layar yang ada

```bash
$ xrandr --listmonitors

Monitors: 1
0: +LVDS1 1366/277x768/156+0+0  LVDS1
```

Memutar tampilan monitor

```bash
$ xrandr --output LVDS1 --rotate left
$ xrandr --output LVDS1 --rotate right
$ xrandr --output LVDS1 --rotate normal
$ xrandr --output LVDS1 --rotate inverted
```

Dicatat biar tidak lupa.