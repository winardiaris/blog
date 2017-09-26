---
id: 101
title: cara buat XML di PHP
date: 2015-06-26T00:08:20+00:00
author: winardiaris
layout: post
guid: http://arwin.my.id/blog/?p=99
permalink: /cara-buat-xml-di-php/
dsq_thread_id:
  - "5130734466"
categories:
  - Catatan
  - PHP
---
```
$query = mysql_query("SELECT * FROM `biodata` ")or die(mysql_error());

$xml =newSimpleXMLElement(<xml>');
while($data=mysql_fetch_array($query)){
    $biodata = $xml->addChild('biodata');
    $biodata->addChild('nama',$data['nama']);
    $biodata->addChild('alamat',$data['alamat']);
}

Header('Content-type: text/xml');
print($xml->asXML());
```