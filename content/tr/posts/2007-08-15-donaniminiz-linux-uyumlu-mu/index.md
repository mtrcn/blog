---
title: "Donanımınız Linux uyumlu mu?"
slug: "donaniminiz-linux-uyumlu-mu"
date: 2007-08-15
---

![](images/Tuxsit3-shine.gif) Eğer bilgisayarınıza \[\[Linux\]\] kurmayı düşünüyor ve internet'te bu konuda biraz araştırma yaptıysanız karşınıza çoğunlukla donanım uyumluluğu ile ilgili problemler çıkacaktır. Fakat şu son on yılda Linux donanım uyumluğu konusunda çok büyük ilerleme sağladı diyebilirim. Kendimden örnek vermek gerekirse; yeni aldığım dizüstü bilgisayarımın ekran kartının ilk denememde sürücüsü olmadığından iki ay kurmamamıştım fakat kullandığım dağıtım \[\[ek:kernel\]\] sürümünü güncelleyince kurmadığım sürücüyü Windows'tan daha kolay kurulabilindiğini gördüm. Eğer linux donanımınızı destekliyorsa emin olun kurması Windows'tan çok daha kolay öyle ki yeniden başlatma derdi yok :)

Bu yazıda yeni bilgisayar almayı düşünen ve bu bilgisayarın Linux uyumlu olmasını isteyenler için yada var olan biligisayarına Linux kurmak isteyenlerin donanım ile ilgili kafanlarında oluşabilecek sorulara yanıt verecek sitelere yer vereceğim.

<!--more-->

**Ekran Kartları**

Ekran katınızın uyumluğunu kontrol etmek için başlıca iki yolunuz var. En çok bilinen ve kullanılan ücretsiz sürücü olan X.org'un listesine bakabilirsiniz. Fakat ücretsiz sürücüyi kullanmak kartınızdan 3D performansı tam olarak alamamanıza neden olucaktır bu durumda en iyisi kart üreticisiniz sitesinden gerekli sürücüyü indirip kurmaktır. Bir çok insanın kullandığı [ATI](http://ati.amd.com/support/driver.html) ve [Nvidia](http://www.nvidia.com/object/unix.html) ekran kartı üreticilerinin sitelerine bakabilirsiniz. Şu sıralar geliştirilmekte olan ve ekran kartı sürücü problemlerini ortandan kaldırmayı hedefleyen umut verici projeler var. Bunlardan [Nouveau](http://nouveau.freedesktop.org/wiki/) projesi Nvidia için çalışırken [Avivo](http://gitweb.freedesktop.org/?p=avivo/xf86-video-avivo.git;a=summary) ATI kartlar için çalışıyor.

\[\[Ubuntu\]\], \[\[Fedora\]\], \[\[Debian\]\], \[\[Pardus\]\] gibi ücretsiz dağıtımlardan birini kurduğunuzda ekran kartınızı kendiliğinden tanıyabilir. Eğer tanımazsa X.org'un standart sürücüsüyle kartınızı kullanmanız yine mümkün.

**Ses Kartları**

Ses kartı uyumluğu hakkında size detaylı bilgi verebilecek tek bir site yok. Kısaca ses kartı konusunda Linux ne durumda diye bakmak için [bu siteyi](http://linux-sound.org/hardware.html) kullanabilirsiniz. Diğer bir kaynak olarakda kullanmak istediğiniz üreticilerin sitelerindeki forumlara bakmanızı öneririm o forumlar bulamayacağınız şey yok :) "Linux'ta Ses" dendiğinde herkesin aklına gelen ALSA (Advanced Linux and Sound Architecture) projesi neredeyse her kart ve modeli için sürücü sunmakta. [ALSA'nn Wiki](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)'sine hangi katları desteklediğine bakabilirsiniz. Eğer karınızı o listede bulamdıysanız yada "Notes" kısımı boşsa bekleyin mutlaka yeni sürümlerinde desteklenecektir.

**Yazıcılar**

Elinizde basit özelliklerde bir yazıcı varsa yada böyle bir yaıcıyı almayı düşünüyorsanız PostScripts(Yazdırma Dili) sayesinde Linuz'ta sorunsız kullanabilirsiniz. Eğer çok özellikli bir yazıcı almayı düşünüyorsanız Linux Vakfı'nın sitesindeki [Desteklenen Yazıcılar Veritabanı](http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro)'nı inceleyin. Eğer Hewlett-Packard yazıcı kulanıyorsanız üreticinin sitesinde büyük olasılıkla Linux sürücünüzü bulabilirsiniz.

**Tarayıcılar**

Eğer tarayıcınız çok fonksiyonlu bir yazıcıda ise yukarıda bahsettiğim veritabanına bakabilirsiniz. Yinede bu konuda en büyük desteği SANE projesi sunuyor kuşkusuz. Projenin [arama motorunda](http://www.sane-project.org/cgi-bin/driver.pl) kendi tarayıcınızı arayabilir ve "complete" (desteklendiği anlamına gelir) yada "unsupported" (desteklenmediği anlamına gelir) iki sonuçtan birini alabilirsiniz. Fakat bu arama moturu sizde çok detay bilgiler isteycektir bu bilgileri nasıl bulacağınız bilmiyorsanız SANE'nin forumlarına göz atın.

**Kabosuz Ağ Kartları (Wireless LAN Kartları)**

Bundan bir kaç yıl önce Linux kullanıcıları Modem tanımta sorunlarıyla boğuşuyolardı neyseki günümüzde hayatımıza giren ADSL yada KabloNET gibi hizmetler sayesinde kullandığımız donanım türeleride değişti ve Linux için bu sprunlar geride kaldı. Her ne kadar modem sorunlarını geride bıraktıysak da kablosuz ağ kartı üreticileri üürettikleri aynı modele farklı Firmware yüklediklerinde dolayı çıkan uyumsuzluk sorunları Linux kullanıcılarına yeni problemler oluşturmakta. Bu kartların uyumluluğunu kontrol edebileceğiniz güncel ve en iyi site için [tıklayın](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/). Eğer kartınızı bu sitede bulamıyorsanız [ndiswrapper](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) sürücünü yada Broadcom kartları için çıkan [bcm43xx-fwcutter](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) sürücüsünü deneyin.

**Taşınabilir Cihazlar**

Taşınabilir cihazların (dizüstü, pda, cep telefonu, GPS) uyumluluklarını kontrol edebileceğiniz [Tuxmobil](http://tuxmobil.org/) sitesini tavsiye ederim. Sadece dizüstü için [Linux-on-Laptop](http://www.linux-laptop.net/) sitesine bakabilirsiniz.

**Diğer Donanımlar ve Adresler**

Yukarıda bahsetmediğim bir donanım için sürücü arıyorsanız yada tüm donanımları içeren sitelere göz atmak istiyorsanız bakabilceğiniz siteler şunlar;

- [Linux Hardware.org](http://www.linuxhardware.org/)
- [Linux Devices](http://www.linuxdevices.com/)
- [Hardware4Linux](http://hardware4linux.info/)

**Sonuç**

Linux için donanım kurmak özellikle kurmak istediğiniz donanım çok yeniyse sıkıntılı olabiliyor ama yinede bu sıkıntının hep süreceği anlamına gelmiyor. Linux geliştiricileri sürekli yeni donanım sürücülerini kullanıma sunmakta. Eğer yukarıda anlattığım sitelerden donanımları nasıl kuracağınızı bilmiyorsanız mutlaka Linux dağıtımlarının forumlarına göz atın çünkü sizin yaşadığınız problem daha önce oraya yazılmış olabilir.
