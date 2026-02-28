---
title: "GClientGeocoder sınıfı ile adres bulma"
slug: "gclientgeocoder-sinifi-ile-adres-bulma"
date: 2008-10-23
---

[Google Geo Developers Blog'ta yazılan yazı](http://googlegeodevelopers.blogspot.com/2008/10/geocoding-in-reverse.html) bizlere artık Google Maps API ile kullanıcıdan aldığımız koordinatları da adrese çevirebileceğimizi müjdeliyor. Geocode Reverse olan bu işlem eskiden adres bilgisini koordinata çevirirken kullandığımız sınıfın getLatLng fonksiyonunun işlevinin tersini getLocations fonksiyonu ile yapabiliyoruz.

![](images/2008-10-24_001126.jpg "GClientGeocoder")

Peki bu ne işimize yarar?

Bu sayede kullanıcıdan belirli bir standartta adres verisi toplayabiliriz. Kullanıcıdan adres bilgisini yazmasını istemek yerine harita üzerinden bulunduğu konumu seçtirerek adres ve koordinatlarını saklayabiliriz. Bu şekilde kullanıcı veritabanında adres verileri ile bilgi üretmek daha kolay olur.

Örnek: Varsayaım yaptığımız uygulamada kullanıcını adres girmesini istiyoruz. Bu bilgiyi metin kutusuna yazmak yerine küçük bir Google Maps alanı üzerinden [bu adresteki](http://gmaps-samples.googlecode.com/svn/trunk/geocoder/reverse.html) gibi harita üzerine tıklayarak belirleyecek. Bu şekilde hem standartize edilmiş adres hemde koordinat bilgisi elde etmiş oluyoruz.

Temelde bu sınıfın bu özelliğini kullanarak çalışan örnek bir uygulama ise [MeetWays](http://meetways.com/). Bu Site sayesinde buluşcağınız kişi ile sizin konumunuzun tam ortasında bir restaurant buluyor. Böylece zamandan kazanıyorsunuz.[](http://meetways.com/)
