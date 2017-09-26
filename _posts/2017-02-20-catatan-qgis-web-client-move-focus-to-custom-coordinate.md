---
id: 334
title: '[catatan] QGIS Web Client move focus to Custom Coordinate'
date: 2017-02-20T21:25:25+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=334
permalink: /catatan-qgis-web-client-move-focus-to-custom-coordinate/
dsq_thread_id:
  - "5568557249"
image: /wp-content/uploads/2017/02/Screenshot_2017-02-20_21-24-13.png
categories:
  - Catatan
  - Catetan
  - QGIS
tags:
  - Catatan
  - catetan
  - custom focus
  - move focus
  - qgis
  - web client
---
Pada QGIS Web Client saya menggunakan Projeksi `EPSG:4326` dan `maxScale:250, minScale:7221282` pada bagian `MapOptions`

tambahkan sedikit script di bawah ini pada `site/js/Customizations.js`:

```js
function dispatch(target, eventType, charCode) {
   var evt = document.createEvent("KeyboardEvent");
   evt.initKeyEvent(
    eventType,
    true,
    true,
    window,
    false,
    false,
    false,
    false,
    charCode,
    0
   );
  target.dispatchEvent(evt);

}
//disini saya mengubah posisi default ke papua
function moveToPapua(){
  var id = document.getElementById("CoordinateTextField");
  id.value = "136,-4"; //titik koordinat
  id.focus();

  id.onkeydown = id.onkeyup = id.onkeypress = function() {console.log(arguments)}

  dispatch(id, 'keydown', 13);
  dispatch(id, 'keyup', 13);
  dispatch(id, 'keypress', 13);
  dispatch(id, 'textinput', 13);
}
```

ubah pada fungsi `customBeforeMapInit` menjadi seperti ini:

```js
function customBeforeMapInit() {
  window.setTimeout(moveToPapua, 3000);
}
```

Salam,

Aris Winardi