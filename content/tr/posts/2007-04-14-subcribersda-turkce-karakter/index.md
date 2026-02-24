---
title: "Subcribers&#8217;da Türkçe Karakter"
date: 2007-04-14
---

\[\[Wordpress\]\] Subcribers 2 eklentisinde gönderdiğim maillerde Türkçe karakterler düzgün görünmediğine dair birkaç arkadaşımdan e-posta aldım. Kendim Gmail kullandığım için böyle bir şey söz konusu değildi fakat Hotmail, Yahoo kullanınca bu sorunun oluştuğunu gördüm.

<!--more-->

Eğer sunucunuzda iconv eklentisi kurulu ise subscribe2.php dosyasının 286. satırından sonra;

`$message = iconv(get_option('blog_charset'),'ISO-8859-9',$message);`

kodunu ekleyin.

Eğer kurulu değilse subscribe2.php dosyasının 286. satırından sonra;

`$yeni = array("i", "c", "g","u","s","o","I","G","U","S","O","C"); $eski = array("ı", "ç", "ğ","ü","ş","ö","İ","Ğ","Ü","Ş","Ö","Ç"); $message = str_replace($eski, $yeni, $message); $subject = str_replace($eski, $yeni, $subject);`

ekleyin.

Türkçe karakterleri silip yerine İngilizce karakterleri koyacaktır.

Sorun çözüldü :)
