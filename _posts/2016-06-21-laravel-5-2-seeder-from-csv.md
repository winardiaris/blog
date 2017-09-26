---
id: 61
title: Laravel 5.2 Seeder from csv
date: 2016-06-21T20:04:51+00:00
author: winardiaris
layout: post
guid: http://www.winardiaris.xyz/?p=61
permalink: /laravel-5-2-seeder-from-csv/
dsq_thread_id:
  - "4927468180"
categories:
  - Catetan
  - Laravel
  - PHP
---
Tambahkan module league/csv

<pre class="brush: bash; title: ; notranslate" title="">$ composer require league/csv
</pre>

berikut contoh kodenya<!--more-->

<pre class="brush: php; title: ; notranslate" title="">&lt;?php 
use Illuminate\Database\Seeder; 
use League\Csv\Reader; 

class DataCountrySeeder extends Seeder 
public function run() { 
$file = public_path().'/data/data_country.csv'; 
$csv = Reader::createFromPath($file);
$nbInsert = $csv-&gt;each(function ($row)  {
      if(empty($row)) return false;
        
      return  \DB::table('data_countries')-&gt;insert(
          array(
            'country_id' =&gt; $row[0],
            'country_name' =&gt; $row[1], 
          )
                  
        );
      });
    }
}
</pre>