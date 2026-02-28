---

title: "OGC'den yeni bir standart: GeoSMS"
slug: "ogcden-yeni-bir-standart-geosms"
date: 2010-05-22
---

![](images/GM-parking-2-150x150.png "geoSMS")Konuma dayalı servislerin hayatımıza her geçen gün daha fazla girmesiyle birlikte mobil yazılımlar tarafından üretilen konum bilgilerinin başka bir mobil yazılıma SMS aracılığı ile gönderilmesi ve o yazılımın bu mesajı alınması doğal olarak gündeme geliyor. Buradaki sorun iki farklı yazılımın nasıl SMS üzerinden haberleşeceği çünkü burada bir standardın olması gerekiyor.

Mekansal bilişimde verinin tutulması ve paylaşılması konularında standartlar üreten OGC(Open Geospatial Consortium) ve Tayvanlı bir firma GeoSMS standardını geliştirdiler.

Bu standartlara göre A, B, E,P ve Q tipinde beş farklı formatta konum içeren SMS tanımlanıyor.

Bu beş formata ait örnekler;<!--more-->

**B(Basic)-Tipi:**

_GeoSMS/2;2235.739,N;12133.851,E;**B**;_

Bu mesaj basit tipte konum bilgisi içeren bir mesaj. Bu mesajda;

GeoSMS/2; GeoSMS standardına ait versiyonu,

2235.739,N; ve 12133.851,E; koordinat bilgisini,

B; format tipini tanımlıyor. Bu düzen diğer dört tip için de aynı.

**A(AGPS)-Tipi:**

_GeoSMS/2;2504.8015,N;12133.9766,E;**A**;ID/x/x/…_

Bu format yardımlı-GPS(şebeke servisi kullanan) ile alınan konum bilgisini baz istasyonuna ait ID numarası ile birlikte tanımlar.

**E(Extended)-Tipi:**

_GeoSMS/2;2504.8015,N;12133.9766,E;**E**;ID/x/x/…_

Bu tip için 5. elemandan sonra kullanılan tanımlar keyfi seçilebilir ve taksimlere ayrılarak yazılır.

**Q(Query)-Tipi:**

_GeoSMS/2;Null;Null;**Q**;Akşam sinemaya gelir misin?_

Bu mesajı alan alıcı uygulamanın "Akşam sinemaya gelir misin?" mesajı göstermesi ve kullanıcının onayı durumunda ise gönderene alıcının koordinatlarını göndermesi bekleniyor.

**P(POI)-Tipi:**

_GeoSMS/2;2504.8015,N;12133.9766,E;**P**;ISIM/TELEFON/ADRES/ACIKLAMA_

5\. elemandan sonraki kısımlar taksimler ile ayrılmış mekan hakkında bilgileri içeriyor olmalı.

Detaylı bilgi için: [http://portal.opengeospatial.org/files/?artifact\_id=36261](http://portal.opengeospatial.org/files/?artifact_id=36261)
