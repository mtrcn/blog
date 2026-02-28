---
title: "Ubuntu DVD/CD ile Grub'u tekrar yüklemek"
slug: "ubuntu-dvdcd-ile-grubu-tekrar-yuklemek"
date: 2009-05-01
---

![](images/windows-vs-linux.jpg "windows-vs-linux")

Windows'u yeniden kurmak zorunda kaldığınızda en çok korkutan şey Ubuntu'yu açmak için kullandığımız Grub'u uçurmak oluyor. Ancak Grub'u yeniden kurmak eskisi kadar zor değil. Eğer elinizde bir Ubuntu DVD/CD'si varsa (sürümü önemli değil) aşağıdaki adımları uygulayarak tekrar kolayca yükleyebiliriz.

1. Ubuntu DVD/CD ile bilgisayarı başlatarak Ubuntu'yu DVD/CD'den açın.
2. Terminal'i açıp **sudo grub** komutunu verin.
3. grub> konsolu açıldığında **find /boot/grub/stage1** komutunu verin. Bu size ekranda (hd0,6) gibi bir sonuç verir.
4. 3\. adımda alacağınız sonuca uyarak **root (hdx,y)** komutunu verin. Burada x ve y değişkenleri 3. adımda alacağınız sonuca göre değişecektir.
5. **setup (hd0)** komutu vererek eski Grub'unuzu MBR'ye yüklemiş olursunuz.
6. grub> konsolundan çıkmak için **quit** komutu verin ve bilgisayarı yeniden başlatıp sonucu görün!

İşte eski Grub'unuza kavuştunuz.
