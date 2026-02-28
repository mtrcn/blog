---

title: "USB'den Windows XP/Vista/7 Kurmak"
slug: "usbden-windows-xpvista7-kurmak"
date: 2009-08-15
---

**13 Kasım 2010 Güncellemesi:**

Aşağıda ilk anlattığım yöntem hâla geçerliliğini korusa da daha kolay bir yöntem buldum. Artık sorun olan bu işlem WinToFlash isimli program ile 4 adımda kolayca tamamlanıyor.

1. Windows DVD/CD'sini optik sürücünüze takın. WinToFlash isimli programı çalıştırın ve "Windows Setup Transfer Wizard"a ve Next butonuna sırasıyla tıklayın.
2. Sizden iki farklı yol göstermenizi isteyen bir pencere daha çıkacak. Burda "Windows files path"e Windows DVD/CD'sinin bulunduğu optik sürücüyü diğerine ise USB sürünücü gösterin.
3. "Windows Lisans Sözleşmesi" çıkacak bunu kabul edin ve geçin.
4. USB diskinizin formatlanacağına dair bir uyarı penceresi çıkacak buna da "OK" diyerek işlemi tamamlayın.

İndirmek için: [http://www.wintoflash.com](http://www.wintoflash.com/)

\---

USB'den Windows kurmak sanıldığının aksine karmaşık bir iş değildir. Eğer elinizden Windows CD/DVD'si varsa veya ISO dosyası mevcutsa bunu yapabilirsiniz. USB'den Windows işletim sistemi kurmada en önemli nokta USB diskinizin biçimlendirilmesidir. Bunu komut satırından da yapabilirsiniz ama ben size bunu en kolay nasıl yaparsınız onu anlatacağım.

1. RMPREPUSB programını [bu adresten](http://www.boot-land.net/forums/index.php?showtopic=7739) (veya [mtrcn.com üzerinden](http://www.mtrcn.com/RMPrepUSB_1.9.75.zip)) indirebilirsiniz. İndireceğiniz Zip dosyasını bir yere açın.
2. RMPREPUSB uygulamasını çalıştırın**.** _Not: Windows Vista'da uygulamayı açmak için sağ tıklayarak "Yönetici olarak çalıştır ( Run as administrator)" seçeneği ile açın._

[![Bootable USB'nin hazırlanışı](images/2009-08-15_102448-300x235.jpg "Bootable USB'nin hazırlanışı")](http://www.mtrcn.com/wp-content/uploads/2009/08/2009-08-15_102448.jpg)

<!--more-->

1. Eğer ISO yada başka bir imaj dosyası kullanacaksanız bunu [PowerISO](http://www.poweriso.com/) yada [Daemon Tools](http://www.daemon-tools.cc/eng/downloads) gibi bir programla imajı açın. Eğer formatı ISO ise tavsiyem [7-Zip](http://www.7-zip.org/) ile ISO dosyasını bir klasöre çıkartmaktır.
2. Program ekranında seçili olması gereken seçenekler şöyle:

- Eğer 2GB'tan büyük bir disk ile çalışacaksanız **FAT32** değilse **NTFS** kullanın.
- **Boot as HDD** seçili olsun.
- XP için **XP bootable**, Vista/7 için **WinPE/Vista v2 bootable** seçili olsun.

1. **Choose Folder** ile imaj dosyanızı açtınığını klasörü yada CD/DVD sürücünüzü seçin. Yanındaki kutucuğun işaretli olduğuna emin olun.
2. Prepare Drive butonu basın ve bekleyin. _Karşınıza çıkacak sorulara OK cevabı verebilirsiniz._
3. _Bilgisayarı USB'den başlatın ve kuruluma başlayın!_

[**USB'den Linux İşletim Sistemi Kurmak İçin Tıklayın!**](http://www.mtrcn.com/usbden-isletim-sistemi-kurmak/)
