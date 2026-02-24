---
title: "Apache 2.2 ile Tomcat 6 üzerine mod_jk kurulumu"
date: 2010-08-18
---

Bu yazıda kurulu Apache Tomcat ve Apache HTTP sunucusu arasındaki köprüyü sağlayan mod\_jk modülünün nasıl kurulacağını anlatmaya çalışacağım.

Kurulumu yapacağım sistemde CentOS 5.4 64 bit işletim sistemi, Apache Tomcat 6.0.9 ve Apache 2.2.3 kurulu. Ayrıca bilgi olması açısından Plesk 9.3 kontrol paneli de bulunmakta.

```
Apache Tomcat dizinim: /usr/tomcat
Apache dizinim: /etc/httpd/
Plesk Domain ayar dosyası: /var/www/vhosts/deneme.com/conf/httpd.include
```

**Uyarı:** Eğer Tomcat'e subdomain (örn: tomcat.deneme.com) üzerinden erişmek istiyorsanız, Plesk veya CPanel kullanıcısı iseniz bunu kurulama başlamadan yapın çünkü kurulumu tamamladıktan sonra yaparsanız bu paneller yaptığımız bazı ayarları silecektir.

[Bu adresten](http://www.apache.org/dist/tomcat/tomcat-connectors/jk/binaries/linux/) güncel mod\_jk modülünü so uzantılı şekilde indirin ve mod\_jk.so şeklinde Apache dizininizin modules klasörü altına taşıyın. Ben bu işlemi Apache dizinimde ki modules klasörü altında yapıyorum.

```
cd /etc/httpd/modules/
wget  http://www.apache.org/dist/tomcat/tomcat-connectors/jk/binaries/
linux/jk-1.2.28/x86_64/mod_jk-1.2.28-httpd-2.2.X.so
mv mod_jk-1.2.28-httpd-2.2.X.so mod_jk.so
```

<!--more--> Ayrıca mod\_jk ayarlarını yapabileceğim ve mod\_jk log kayıtlarının tutulacağı dosyalarını oluşturuyorum.

```
touch /etc/httpd/conf/worker.properties
touch /etc/httpd/mod_jk.log
```

_worker.properties_ dosyasını _nano_ (düzenleme programı) ile açıp gerekli düzenlemeleri yapıyorum.

```
 nano /etc/httpd/conf/worker.properties
```

```
worker.list=worker1
# worker1 (ajp13) ayarları
worker.worker1.type=ajp13
worker.worker1.host=localhost
worker.worker1.port=8009
worker.worker1.socket_keepalive=1
worker.worker1.socket_timeout=300
```

Şimdi Apache üzerinde yapacağımız değişikliklere sıra geldi. httpd.conf dosyasını _nano_ ile açıyoruz ve aşağıdaki satırları ekliyoruz.

```
 nano /etc/httpd/httpd.conf
```

```
LoadModule jk_module modules/mod_jk.so
JkWorkersFile /etc/httpd/conf/workers.properties
JkLogFile     /etc/httpd/logs/mod_jk.log
JkLogLevel    info
```

Ayrıca ilgili etiketini buluyoruz ve aşağıdaki satırı etiketinden önce ekliyoruz. subdomain için;

```
JkMount /* worker1
```

subdomain için kullanmayacaksınız:

```
JkMount /tomcat/* worker1
```

Son olarak Tomcat için gerekli ayarları _server.xml_ dosyasında yapıyoruz.

Kurulum tamamlandı eğer yanlış giden bir şeyler yoksa Tomcat sunucunuza; Subdomain için ayarladıysanız; http://tomcat.deneme.com veya ayarlamadıysanız, http://www.deneme.com/tomcat ile artık ulaşabilirsiniz.
