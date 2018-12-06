---
title: 'Phpmyadmin - count(): Parameter must be an array or an object that implements Countable'
date: 2018-12-06T17:00:00+00:00
author: winardiaris
layout: post
permalink: /phpmyadmin-count-parameter-must-be-an-array-or-an-object-that-implements-countable/
image: https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/PhpMyAdmin_logo.svg/1000px-PhpMyAdmin_logo.svg.png
categories:
  - Catatan
  - Catetan
  - Linux
  - Debian
  - phpMyAdmin
---

![phpMyAdmin](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/PhpMyAdmin_logo.svg/1000px-PhpMyAdmin_logo.svg.png "phpMyAdmin")  

# Tulisan ini untuk pengingat diri

- Edit berkas:  

  ```bash
  /usr/share/phpmyadmin/libraries/sql.lib.php
  ```

- Ganti:  

  ```php
  (count($analyzed_sql_results['select_expr'] == 1)
  ```

- dengan:

  ```php
  (count($analyzed_sql_results['select_expr']) == 1
  ```

## Cara cepat

  ```bash
  sudo sed -i "s/|\s*\((count(\$analyzed_sql_results\['select_expr'\]\)/| (\1)/g" /usr/share/phpmyadmin/libraries/sql.lib.php
  ```

Salam.