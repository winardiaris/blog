---
id: 233
title: Cara custom domain WordPress Openshift
date: 2016-03-23T01:20:36+00:00
author: winardiaris
layout: post
guid: http://arwin.my.id/blog/?p=233
permalink: /cara-custom-domain-wordpress-openshift/
dsq_thread_id:
  - "5221843102"
categories:
  - Catatan
---
#### Tahap 1 : Mendaftar di Cloudflare

Silahkan masuk kehalaman <a href="https://www.cloudflare.com/a/sign-up" target="_blank">ini</a>,  lewati dan Login jika anda sudah menpunyai akun di Cloudflare

#### Tahap 2 : Konfigurasi Cloudflare

<p style="text-align: center;">
  klik Add site lalu isikan nama domain ang telah anda daftarkan.<a href="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-add-site-1458628709239.png"><img class="alignnone size-full wp-image-236" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-add-site-1458628709239.png?resize=700%2C459" alt="screencapture-www-cloudflare-com-a-add-site-1458628709239" data-recalc-dims="1" /></a><small>Gb. 01</small>
</p>

klik menu DNS isikan name dengan nama domain anda, dan Ipv4 dengan ip blog anda yang di openshift (blog-winardiaris.rhcloud.com => 54.172.219.155)

<pre class="brush: bash; title: ; notranslate" title="">$ ping blog-winardiaris.rhcloud.com
PING ec2-54-172-219-155.compute-1.amazonaws.com (54.172.219.155) 56(84) bytes of data.
64 bytes from ec2-54-172-219-155.compute-1.amazonaws.com (54.172.219.155): icmp_seq=1 ttl=39 time=261 ms
64 bytes from ec2-54-172-219-155.compute-1.amazonaws.com (54.172.219.155): icmp_seq=2 ttl=39 time=261 ms
64 bytes from ec2-54-172-219-155.compute-1.amazonaws.com (54.172.219.155): icmp_seq=3 ttl=39 time=261 ms
64 bytes from ec2-54-172-219-155.compute-1.amazonaws.com (54.172.219.155): icmp_seq=4 ttl=39 time=260 ms
^C
--- ec2-54-172-219-155.compute-1.amazonaws.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 260.900/261.092/261.223/0.380 ms
</pre>

<p style="text-align: center;">
  <a href="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-2-1458166994637.png"><img class="alignnone size-full wp-image-237" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-2-1458166994637.png?resize=700%2C578" alt="screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-2-1458166994637" data-recalc-dims="1" /></a><br /> <small>Gb. 02</small>
</p>

klik _Continue ,_ pilih  Free Website

<p style="text-align: center;">
  <a href="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-3-1458167028310.png"><img class="alignnone size-full wp-image-238" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-3-1458167028310.png?resize=700%2C574" alt="screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-3-1458167028310" data-recalc-dims="1" /></a><small>Gb. 03</small>
</p>

klik continue dan anda akan mendapatkan _CloudFlare Nameservers_ yang harus anda salin dan tempel di tempat anda membeli domain ( saya membeli di rumahweb)

<p style="text-align: center;">
  <a href="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-4-1458167040473.png"><img class="alignnone size-full wp-image-239" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-4-1458167040473.png?resize=700%2C510" alt="screencapture-www-cloudflare-com-a-setup-winardiaris-xyz-step-4-1458167040473" data-recalc-dims="1" /></a>
</p>

<p style="text-align: center;">
  <small>Gb. 04</small>
</p>

#### Tahap 3 : Konfigurasi Rumahweb

Masuk _Client Area _lalu pilih menu _Nameservers ._

  * <span style="color: #333333;">Klik Gunakan nameservers lain (masukkan dibawah ini)</span>
  * Isikan Nameservers sesuai pada gambar 04

<p style="text-align: center;">
  <a href="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-clientzone-rumahweb-com-clientarea-php-1458167069738.png"><img class="alignnone size-full wp-image-241" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-clientzone-rumahweb-com-clientarea-php-1458167069738.png?resize=700%2C532" alt="screencapture-clientzone-rumahweb-com-clientarea-php-1458167069738" data-recalc-dims="1" /></a><small>Gb. 05</small>
</p>

<p style="text-align: center;">
  <a href="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-clientzone-rumahweb-com-clientarea-php-1458167123751.png"><img class="alignnone size-full wp-image-242" src="https://i1.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-clientzone-rumahweb-com-clientarea-php-1458167123751.png?resize=700%2C532" alt="screencapture-clientzone-rumahweb-com-clientarea-php-1458167123751" data-recalc-dims="1" /></a><small>Gb. 06</small>
</p>

#### Tahap 4: Konfigurasi Worpress

Masuk ke dashboard Blog wordpress anda Pilih Menu Settings => General
  
Lalu isikan WordPress Address (URL) dan Site Address (URL) sesuai gambar 02

[<img class="alignnone size-full wp-image-245" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-220316-175059.png?resize=700%2C394" alt="Screenshot - 220316 - 17:50:59" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/Screenshot-220316-175059.png)<small>Gb. 07</small>

#### Tahap 5 : Konfigurasi Openshift

  * Masuk Dashboard Openshift
  * klik Menu Application
  * klik Aplikasi (disini blog-winardiaris.rhcloud.com)
  * klik change alias
  * isikan Domain sesuai gambar 02

[<img class="alignnone size-full wp-image-246" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application-56e14acd2d5271cc310000f6-blog-aliases-new-1458644123494.png?resize=700%2C542" alt="screencapture-openshift-redhat-com-app-console-application-56e14acd2d5271cc310000f6-blog-aliases-new-1458644123494" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-openshift-redhat-com-app-console-application-56e14acd2d5271cc310000f6-blog-aliases-new-1458644123494.png)<small>Gb. 08</small>

#### Tahap 6: Cek Domain

Masuk <a href="http://www.winardiaris.xyz" target="_blank">www.winardiaris.xyz</a>

[<img class="alignnone wp-image-255 size-full" src="https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-winardiaris-xyz-1458670699925.png?resize=700%2C938" alt="" data-recalc-dims="1" />](https://i0.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-winardiaris-xyz-1458670699925.png)

Catatan :
  
Tunggu waktu propagansi oleh Cloudflare sekitar 10-30menit. jika belum berhasil silahkan cek kembali konfigurasi anda.
  


* * *

#### Tahap Tambahan 1 : Men-redirect winadiaris.xyz ke www.winardiaris.xyz

  * Masuk ke dashboard cloudflare
  * Klik menu Page Rules
  * Isikan URL Pattern dengan http://winardiaris.xyz (url asal)
  * Pilih Domain Forwading
  * Isikan Destination URL dengan http://www.winardiaris.xyx (url tujuan)

[<img class="alignnone size-full wp-image-253" src="https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-page-rules-winardiaris-xyz-1458200193244.png?resize=700%2C557" alt="screencapture-www-cloudflare-com-a-page-rules-winardiaris-xyz-1458200193244" data-recalc-dims="1" />](https://i2.wp.com/www.winardiaris.xyz/wp-content/uploads/2016/03/screencapture-www-cloudflare-com-a-page-rules-winardiaris-xyz-1458200193244.png)
  


* * *

#### Tahap Tambahan 2 : Menonaktifkan SSL pada WordPress.

Masuk folder tempat anda mengklon git ( lihat pada tutorial <a href="http://www.winardiaris.xyz/2016/03/10/cara-deploy-wordpress-di-openshift/" target="_blank">ini</a>)

$ cd /var/www/html/blog

Ubah pada .openshift/config/wp-config.php

$ vi .openshift/config/wp-config.php

cari

<pre class="brush: bash; title: ; notranslate" title="">define('FORCE_SSL_ADMIN', true);</pre>

ubah menjadi

<pre class="brush: bash; title: ; notranslate" title="">define('FORCE_SSL_ADMIN', false);</pre>

simpan dan push ke git openshift

<pre class="brush: bash; title: ; notranslate" title="">$ git add .
$ git commit -m "force ssl admin false"
[master cd98441] force ssl admin false
 1 file changed, 1 insertion(+), 2 deletions(-)

$ git push
Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 445 bytes | 0 bytes/s, done.
Total 5 (delta 3), reused 0 (delta 0)
remote: Stopping PHP 5.4 cartridge (Apache+mod_php)
remote: Waiting for stop to finish
remote: Waiting for stop to finish
remote: Stopping MySQL 5.5 cartridge
remote: Stopping PHPMyAdmin cartridge
remote: Waiting for stop to finish
remote: Waiting for stop to finish
remote: Building git ref 'master', commit cd98441
remote: Checking .openshift/pear.txt for PEAR dependency...
remote: Preparing build for deployment
remote: Deployment id is 4280c25c
remote: Activating deployment
remote: Starting MySQL 5.5 cartridge
remote: Starting PHPMyAdmin cartridge
remote: Copying WordPress plugins from .openshift/plugins
remote: Copying WordPress themes from .openshift/themes
remote: Copying WordPress languages from .openshift/languages
remote: Database already configured.
remote: Starting PHP 5.4 cartridge (Apache+mod_php)
remote: Application directory "php/" selected as DocumentRoot
remote: -------------------------
remote: Git Post-Receive Result: success
remote: Activation status: success
remote: Deployment completed with status: success
To ssh://56e14acd2d5271cc310000f6@blog-winardiaris.rhcloud.com/~/git/blog.git/
   b124b6f..cd98441  master -&gt; master

</pre>