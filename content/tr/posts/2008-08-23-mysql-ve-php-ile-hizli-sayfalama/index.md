---
title: "MySQL ve PHP ile hızlı sayfalama"
slug: "mysql-ve-php-ile-hizli-sayfalama"
date: 2008-08-23
---

[dmry](http://www.dmry.net) kendi sitesinde MySQL ile nasıl performanslı sayfalama yapılacağını [anlatmış](http://www.dmry.net/mysql-sorgusunda-limit-kullanirken-toplam-satir-sayisini-bulmak). Kendi projelerimde kullanmak üzere hemen denemeye koyuldum ve 3-4 satır koddan kurtuldum ve sorgu süremin kısaldığının gördüm.

dmry'den farklı olarak ben size aşağıdaki kodların nasıl PHP içinde kullanılacağını anlatacağım. Aslında pek fark yok ama işinize yarayabilir diye paylaşıyorum. `SELECT SQL_CALC_FOUND_ROWS sehir_ad, tel_kod FROM sehir WHERE sehir_ad LIKE 'a%' LIMIT 0,2; SELECT FOUND_ROWS();` Bu iki satır kodu sırasıyla; `mysql_query("SELECT SQL_CALC_FOUND_ROWS sehir_ad, tel_kod FROM sehir WHERE sehir_ad LIKE 'a%' LIMIT 0,2"); $sorgu=mysql_query("SELECT FOUND_ROWS()"); $toplam_satir=mysql_fetch_row($sorgu); //Dizi içine atıyoruz. echo $toplam_satir[0]; //ilk eleman bize toplam satırı yazacaktır`
