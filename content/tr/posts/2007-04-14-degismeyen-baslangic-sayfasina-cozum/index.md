---
title: "Değişmeyen Başlangıç Sayfasına Çözüm"
slug: "degismeyen-baslangic-sayfasina-cozum"
date: 2007-04-14
---

Birçok insan değişmeyen Internet Explorer sayfasından şikayet ediyor. Bugüne kadar bir çok tanıdığım insandan bilgisayarlarındaki bu sorunu çözmek için çağırıldım. Sorunu virus'e bağlıyorlar. Aslında tam olarak virus işi değil. \[\[ek:HiJack\]\] olarak adlandırılan trojan benzeri programlar tarafından bu durum meydana gelir.

<!--more-->

Problemin çözümü basittir, aşağıdaki adımları izleyin;

Başlat > Çalıştır 'a girip, "_regedit_" yazın. Ağaç menüden

_HKEY\_CURRENT\_USER\\Software\\Policies\\Microsoft\\Internet Explorer\\Control Panel_

girip _HomePage_'in _Dword_ değerini 1'den 0'a çevirin.

Sorun çözüldü! :)
