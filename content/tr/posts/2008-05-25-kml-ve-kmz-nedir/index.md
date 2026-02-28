---

title: "KML ve KMZ nedir?"
slug: "kml-ve-kmz-nedir"
date: 2008-05-25
---

KML ve KMZ çeşitli yersel bilgilerin (yerimleri, ağ bağlantıları...) kayıtlı tutulmasını sağlayan XML tabanlı [Google Earth](http://earth.google.com/intl/tr/) ile kullanılan dosya formatıdır.

KML açılımı Keyhole Markup Language olan Keyhole - Google 2004'te firmayı satın aldı - firması tarafından keşfedilen daha sonra Googe Earth ile kullanılmaya başladıktan sonra popülerleşen bir dil. Eğer HTML/XML ile daha önce uğraştıysanız dili öğrenmek çok az vakitiniz alıcaktır. Dili öğrenmek için [KML Tutorial](http://www.keyhole.com/kml/kml_tut.html) yada [KML Documentation](http://www.keyhole.com/kml/kml_doc.html) sitelerini kullanabilirsiniz.<!--more-->

> ```
> Örnek:
> <?xml version="1.0" encoding="UTF-8"?>
> <kml xmlns="http://earth.google.com/kml/2.2">
>   <Placemark>
>     <name>Örnek Yerimi</name>
>     <description>Bu yerimini örnek olsun diye oluşturdum.</description>
>     <Point>
>       <coordinates>-122.0822035425683,37.42228990140251,0</coordinates>
>     </Point>
>   </Placemark>
> </kml>
> 
> ```

KMZ ise KML-Zipped olarak geçen aslında KML ile hiç bir farkı olmayan ama KML'nin sıkıştırılmış formatıdır. KMZ'nin en önemli özelliği yerimlerinizi resimler veya ikonlar ilebirlikte saklayabilmenizdir.

![](images/GE_Popular_Zoning_small.jpg)

KML ile neler yapılabileceğini daha iyi anlamak için Portland belediyesininyaptıklarına bakalım. Portland şehir yaptığı GIS çalışmaları ile internete üzerinde şehrin yerleşim, suç, deprem ve yükseltileri gibi bilgilerini KML dosyaları ile paylaşıyor. Dosyalara [buradan](http://www.portlandmaps.com/google.cfm) ulaşabilirsiniz.

![](images/20080525122149oq9.jpg)**[](http://services.google.com/earth/kmz/mohc_defra_layer.kmz)**

**[Climate Change in our World](http://services.google.com/earth/kmz/mohc_defra_layer.kmz)** bu KMZ dosyası ise size dünya üzerindeki iklim değişikliğiyle oluşun sıcaklık değişimrini veriyor.

Daha fazla KML/KMz için [Google Earth KML Galerisine](http://earth.google.com/gallery/index.html) göz atmanızı öneririm.

Sonuç olarak, KML ile programcıların Google Earth'ü kullanarak çeşitli veri sunumları veya GIs uygulamalarını kolayca geliştirlmesi sağlanmış.

**22 Kasım 2008 Güncellemesi:**

Eğer KML komutlarını deneyerek interaktif olarak öğrenmek istiyorsanız [KML Interactive Sampler](http://kml-samples.googlecode.com/svn/trunk/interactive/index.html) uygulaması tam size göre. [Google Earth Plugin](http://code.google.com/apis/earth)'i yükledikten sonra kullanabilirsiniz.
