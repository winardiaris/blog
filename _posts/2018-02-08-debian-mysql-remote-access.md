---
title: 'Debian - MySQL Remote Access'
date: 2018-02-08T01:12:16+00:00
author: winardiaris
layout: post
permalink: /debian-mysql-remote-access/
image: https://upload.wikimedia.org/wikipedia/en/thumb/6/62/MySQL.svg/1200px-MySQL.svg.png
categories:
  - Catatan
  - Catetan
  - Linux
  - Debian
  - MySQL
---

![MySQL](https://upload.wikimedia.org/wikipedia/en/thumb/6/62/MySQL.svg/1200px-MySQL.svg.png "MySQL")  

Tulisan ini untuk pengingat diri

- Buka berkas  
  `/etc/mysql/my.cnf` 
- Ubah bagian  
  `bind-address = 127.0.0.1`
- Jalakan ini di MySQL  
  `GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;`  
 `FLUSH PRIVILEGES;`

Salam.