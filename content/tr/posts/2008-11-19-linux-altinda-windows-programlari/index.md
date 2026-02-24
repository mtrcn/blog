---
title: "Linux altında Windows programları çalıştırmak için 6 ücretsiz araç"
date: 2008-11-19
---

Linux'a geçmeyi düşünenlerin ilk aklına gelen sorudur: acaba Windows'ta kullandığım program Linux'ta çalışır mı? Bu gibi sorunların üstesinden gelmenin iki yolu var, birincisi Microsoft'un Windows'un kaynak kodlarını açmasını beklemek, ikincisi ise emülatör yazılımları kullanmak. Sanırım ikincisi daha kolay ve akla yatkın şimdilik.

Emülatör olarak kullanabileceğimiz 6 program var bunları tek tek anlatalım:

<!--more-->

**1- [Wine](http://www.winehq.org/) (Açık Kaynak Kodlu)**

Geliştiricileri tarafından sürekli yeni sürümleri yayınlanan ve diğer emülatörlerden farklı olan bir yazılım. Bu yazılımı yüklediğinizde ayrıca bir daha Windows kurmanıza gerek yok. Kurduktan sonra [desteklediği Windows programlarını](http://appdb.winehq.org/) tek tıklama ile Linux içinde açmaya hazırsınız demektir. Ayrıca Solaris ve Mac OS X üzerinde de çalışabilir.

**2- [Virtual Box](http://www.virtualbox.org/) (Açık Kaynak Kodlu)**

Geliştiricileri tarafından yine sürekli geliştirilen ama çok yeni bir yazılım. Henüz çıkması üzerinden bir yıl geçti ama oldukça popüler. "Guest OS" olarak tanımaladığı bir veya birden çok işletim sistemi kurabiliyorsunuz. Kurulumu ve kullanımı oldukça basit olan bu yazılımın görünmezlik modu (Seamless Mode) ile kurudğunuz işleim sisteminin sadece görev çubuğu ekranda gözüküyor. Böylece iki işletim sisteminin aynı anda çok daha işlevsel kullanmak mümkün oluyor.

**3- [Qemu](http://bellard.org/qemu/) (Açık Kaynak Kodlu)**

Adını gösterdiği performansla duyurmuş yazılım. "dynamic translation" olarak tanımladığı özelliği ile işlemeciyi bile sanallaştırabiliyor. Ancak bu aksine bir hız değil yavaşlığa neden oluyor bunun yanında avantajı donanım uyumluluğun maksimum sevyede olması.

**4- [Bochs](http://bochs.sourceforge.net/) (Açık Kaynak Kodlu)**

Üstte saydığım emülatörlere göre daha fazla sistem ihtiyacında bulunan bir emülatör. Kurulumuda yeni kullanıcılar için kolay olmayabilir. Ancak tüm donanımı sanallaştırabilir. Ayrıca Windows altında da çalışabiliyor.

**5- [rdesktop](http://www.rdesktop.org/) (Açık Kaynak Kodlu)**

**6-Xen (Bu da Açık Kaynak Kodlu)**

Kurulumu biraz zor olan ancak hızlı bir emülatör. Neredeyse tüm işletim sistemlerini destekliyor ve tüm işlemci mimarilerinde çalışıyor.
