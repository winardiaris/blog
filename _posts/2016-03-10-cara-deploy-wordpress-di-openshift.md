---
id: 6
title: Cara deploy WordPress di Openshift
date: 2016-03-10T12:05:52+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=6
permalink: /cara-deploy-wordpress-di-openshift/
dsq_thread_id:
  - "4684287094"
image: /wp-content/uploads/2016/03/wptoopenshif.png
categories:
  - Tutorial
tags:
  - openshift
  - wordpress
---
#### Tahap 1 : Daftar akun di Openshift

Silahkan masuk ke halaman <a title="Daftar akun" href="https://www.openshift.com/app/account/new" target="_blank">ini</a> untuk mendaftarkan akun, lewati jika sudah mempunyai akun di Openshift

#### Tahap 2 : Setup Kunci Publik _(Public Key)_

Untuk mengkoneksikan komputer anda dengan Openshift membutuhkan kunci publik yang berupa teks kunci yang di simpan di ~/.ssh/id_rsa.pub

Anda perlu menyalin isi berkas id_rsa.pub ke pengaturan di Openshift yang digunakan untuk mengidentifikasi bahwa pada saat anda SSH atau mengunggah kode ke Openshift

cek jika anda sudah punya kunci publik:

<pre class="brush: bash; title: ; notranslate" title="">$ ls ~/.ssh | grep id_rsa.pub </pre>

dan hasil yang keluar

<pre class="brush: bash; title: ; notranslate" title="">$ id_rsa.pub</pre>

berati anda sudah mempunyai kunci publik

Jika anda belum mempunyai kunci publik ketikan perintah berikut :

<pre class="brush: bash; title: ; notranslate" title="">$ ssh-keygen -t rsa </pre>

ketikan perintah berikut untuk menyalin kunci publik anda :

<pre class="brush: bash; title: ; notranslate" title="">$ cat ~/.ssh/id_rsa.pub | xclip </pre>

lalu masuk ke konsol web openshift pada menu setting.  Tempel kunci publik dan simpan.

[<img class="alignnone size-full wp-image-207" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/001-tempel-kunci-publik1.png?resize=700%2C508" alt="001- tempel kunci publik" data-recalc-dims="1" />](https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/001-tempel-kunci-publik1.png)
  
<small>gb . 1</small>

#### Tahap 3: Instalasi WordPress di Openshift

  1. pilih tab _Application_
  2. Klik _&#8220;Create your first application now&#8221;_
  3. ketik wordpress pada kolom pencarian
  4. klik pada &#8220;WordPress 4&#8221;

[<img class="alignnone size-full wp-image-215" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/003-wordpress-.png?resize=700%2C475" alt="003 - wordpress" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/003-wordpress-.png)
  
<small>gb . 2</small>
  
Sekarang dialihkan ke halaman &#8220;Configure the application&#8221;

  * <span style="color: #4b4b4b;">Public URL: Atur alamat blog anda , ini adalah subdomain di bawah rhcloud</span><code class="inline" style="color: #4b4b4b;">.com</code><span style="color: #4b4b4b;">.  Pada kali ini  saya menggunakan blog-<span style="color: #404040;">winardiaris.rhcloud.com .  winardiaris</span></span><span style="color: #4b4b4b;"> nama saya dan blog adalah mana aplikasi</span><span style="color: #4b4b4b;">.</span>
  * Biarkan kolom yang lainnya
  * Klik &#8220;<span style="color: #4b4b4b;">Create application&#8221;</span>

[<img class="alignnone size-full wp-image-217" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/004-konfigurasi-wordpress.png?resize=700%2C754" alt="004 - konfigurasi wordpress" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/004-konfigurasi-wordpress.png)
  
<small>gb . 3</small>
  
setelah selesai akan di alihkan ke halaman yang menandakan deploy telah berhasil.

[<img class="alignnone size-full wp-image-220" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/005-hasil-02.png?resize=700%2C533" alt="005 - hasil 02" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/005-hasil-02.png)
  
<small>gb . 4</small>

Jika ada yang ingin diubah atau ditambahkan pada sumber (source) wordpress anda salin (cloning).
  
ubah pada ssh://xxxxxxxxxxxxx@xxxxxxxx.rhcloud.com/~/git/blog.git/ sesuai dengan url yang yang di hasilkan pada gambar di atas.

<pre class="brush: bash; title: ; notranslate" title="">$ git clone ssh://xxxxxxxxxxxxx@xxxxxxxx.rhcloud.com/~/git/blog.git/
$ cd blog/ </pre>

_catatan : file wordpress ada di folder .openshift (hidden)_

jika telah merubah atau menambahkan ketikan perintah berikut:

<pre class="brush: bash; title: ; notranslate" title="">$ git add .
$ git commit -m 'My changes'
$ git push </pre>

#### Tahap 4 : Konfigurasi wordpress

  * Masuk ke url sesuai pada gambar 3 (http://www.winardiaris.xyz/) [<img class="alignnone size-full wp-image-225" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/006-install-wordpress.png?resize=700%2C326" alt="006 - install wordpress" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/006-install-wordpress.png)
  * Isi sesuai keinginan anda pada kolom berikut: [<img class="alignnone size-full wp-image-226" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/007-setup-wordpress-.png?resize=700%2C437" alt="007 - setup wordpress" data-recalc-dims="1" />](https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/007-setup-wordpress-.png) klik Install WordPress
  * [<img class="alignnone size-full wp-image-227" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/008-sukses.png?resize=700%2C326" alt="008- sukses" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/008-sukses.png) [<img class="alignnone size-full wp-image-228" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/009-login.png?resize=700%2C326" alt="009 - login" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/009-login.png)

Selamat mencoba .