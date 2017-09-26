---
id: 31
title: Cara deploy plain php ke OpenShift
date: 2016-03-29T01:24:36+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=31
permalink: /cara-deploy-plain-php-ke-openshift/
dsq_thread_id:
  - "4701131392"
image: /wp-content/uploads/2016/03/php-to-openshift.png
categories:
  - Tutorial
tags:
  - openshift
  - php
---
#### Tahap 1 : Daftar akun openshift

Silahkan masuk ke halaman <a href="https://www.openshift.com/app/account/new" target="_blank">ini</a> untuk mendaftarkan akun, lewati dan login jika sudah mempunyai akun di Openshift

#### Tahap 2: Tambah aplikasi di openshift

  * Masuk ke halaman konsol _web openshift_ pilih tab application
  * Klik A_dd Application&#8230;_<img class="alignnone wp-image-32 size-full" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-applications-1459186452334.png?resize=700%2C349" alt="screencapture-openshift-redhat-com-app-console-applications-1459186452334" srcset="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-applications-1459186452334.png?w=1366 1366w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-applications-1459186452334.png?resize=300%2C150 300w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-applications-1459186452334.png?resize=768%2C383 768w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-applications-1459186452334.png?resize=1024%2C511 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />
  * Ketik &#8220;php&#8221; pada kolom pencarian<img class="alignnone wp-image-33 size-full" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-290316-003626.png?resize=700%2C394" alt="Screenshot - 290316 - 00:36:26" srcset="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-290316-003626.png?w=1366 1366w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-290316-003626.png?resize=300%2C169 300w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-290316-003626.png?resize=768%2C432 768w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-290316-003626.png?resize=1024%2C576 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />
  * Pilih versi php yang akan digunakan (contoh: PHP 5.4)
  * Sekarang dialihkan ke halaman “Configure the application”
  * Public URL: Atur alamat aplikasi php  anda , ini adalah subdomain di bawah rhcloud<code class="inline">.com</code>.  Pada kali ini  saya menggunakan itung-winardiaris.rhcloud.com .  winardiaris nama saya dan itung adalah nama aplikasi.
  * Biarkan kolom yang lainnya
  * Klik “Create application”<img class="alignnone wp-image-34 size-full" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754.png?resize=700%2C740" alt="screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754" srcset="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754.png?w=1366 1366w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754.png?resize=284%2C300 284w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754.png?resize=768%2C812 768w, https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application_type-cart-php-5-4-1459186626754.png?resize=968%2C1024 968w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />
  * Setelah selesai akan di alihkan ke halaman ini yang menandakan deploy telah berhasil.<img class="alignnone size-full wp-image-35" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?resize=700%2C422" alt="making code change" srcset="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?w=1708 1708w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?resize=300%2C181 300w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?resize=768%2C463 768w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?resize=1024%2C617 1024w, https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/making-code-change.png?w=1400 1400w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />
  * buka terminal lalu ketikan perintah berikut untuk mengkloning git yang dihasilkan openshift <pre class="brush: bash; title: ; notranslate" title="">$ git clone ssh://xxxxxxxxxxxxx@xxxxxxxx.rhcloud.com/~/git/itung.git/
$ cd itung/</pre>

  * salin source code aplikasi anda ke folder yang dihasilkan oleh git clone <pre class="brush: bash; title: ; notranslate" title="">cp -r /folder/aplikasi_php/ /folder/git/aplikasi_php/
</pre>

  * ketikan perintah berukut untuk mengunggah aplikasi anda ke git openshift <pre class="brush: bash; title: ; notranslate" title="">$git add --all
$git commit -m "upload aplikasi ke openshift"
$git push
</pre>

#### Tahap 3 : Cek Aplikasi

Buka url sesuai yang dibuat pada gambar 2 (contoh:<a href="http://itung-winardiaris.rhcloud.com" target="_blank">itung-winardiaris.rhcloud.com</a>)<img class="alignnone size-full wp-image-36" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-itung-winardiaris-xyz-1459188849228.png?resize=700%2C349" alt="screencapture-itung-winardiaris-xyz-1459188849228" srcset="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-itung-winardiaris-xyz-1459188849228.png?w=1366 1366w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-itung-winardiaris-xyz-1459188849228.png?resize=300%2C150 300w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-itung-winardiaris-xyz-1459188849228.png?resize=768%2C383 768w, https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-itung-winardiaris-xyz-1459188849228.png?resize=1024%2C511 1024w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />

#### Tahap tambahan : Konfigurasi Custom domain

Anda bisa lihat di <a href="http://www.winardiaris.xyz/cara-custom-domain-wordpress-openshift-2/" target="_blank">sini</a>

&nbsp;