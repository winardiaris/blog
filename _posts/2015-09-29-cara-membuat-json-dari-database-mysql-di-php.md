---
id: 143
title: Cara membuat json dari database mysql di PHP
date: 2015-09-29T21:17:14+00:00
author: winardiaris
layout: post
guid: http://arwin.my.id/blog/?p=143
permalink: /cara-membuat-json-dari-database-mysql-di-php/
dsq_thread_id:
  - "5182284703"
categories:
  - Catatan
  - PHP
tags:
  - json
  - mysql
  - php
---
<pre class="brush: php; title: ; notranslate" title="">$qry = "SELECT * FROM `post`";
$result	= mysql_query($qry) or die(mysql_error());
$count = mysql_num_fields($result);

$data = array();
$field_name = array();
$field_value = array();

while($d=mysql_fetch_array($result)){
  for($i=0;$i&lt;$count;$i++){
     array_push($field_name,mysql_field_name($result,$i));
     array_push($field_value,$d[$i]);
  }
  
  $combine = array_combine($field_name,$field_value);
  array_push($data,$combine);
}

$json = json_encode($data);
print($json);
</pre>

hasilnya akan seperti ini

<pre class="brush: jscript; title: ; notranslate" title="">[
    {
        "pid": "1",
        "uid": "1",
        "title": "Post 1",
        "post": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec at tortor libero. Nam sit amet tortor velit. Maecenas ac elementum sapien, condimentum scelerisque ex. Nulla aliquam nec erat posuere vulputate. In facilisis hendrerit mauris egestas condimentum. Ut hendrerit ipsum odio, sollicitudin pulvinar mauris pellentesque eu. Integer faucibus, lectus vitae pretium placerat, erat nisl laoreet leo, at eleifend risus sem sed elit. Aliquam ac felis sem. Suspendisse varius enim ac posuere aliquam. Fusce accumsan vel ex nec dictum. Curabitur faucibus odio nec interdum ornare. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.",
        "c_at": "2015-09-10 02:06:14",
        "u_at": "2015-09-23 03:05:18"
    },
    {
        "pid": "2",
        "uid": "1",
        "title": "Post 2",
        "post": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec at tortor libero. Nam sit amet tortor velit. Maecenas ac elementum sapien, condimentum scelerisque ex. Nulla aliquam nec erat posuere vulputate. In facilisis hendrerit mauris egestas condimentum. Ut hendrerit ipsum odio, sollicitudin pulvinar mauris pellentesque eu. Integer faucibus, lectus vitae pretium placerat, erat nisl laoreet leo, at eleifend risus sem sed elit. Aliquam ac felis sem. Suspendisse varius enim ac posuere aliquam. Fusce accumsan vel ex nec dictum. Curabitur faucibus odio nec interdum ornare. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.",
        "c_at": "2015-09-10 03:10:20",
        "u_at": "2015-09-23 05:17:23"
    }
]
</pre>