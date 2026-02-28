---
title: "PHP'de 6 Pratik Regular Expression(Düzenli İfade)"
slug: "phpde-6-pratik-regular-expressionduzenli-ifade"
date: 2009-03-09
---

Kafa karıştırıcı olan ama bir okadar da hayat kurtarıcı önemi olan düzenli ifadeleri PHP'de kullanmak zordur. Her ne kadar zor olsalar da kullanıcının girdiği bilgilerin kontrolü için sık sık kullanılan veya her zaman akla gelmeyen 6 düzenli ifadeyi bu yazıda bulacaksınız.

### #1: Kullanıcı Adı Doğrulama

Kullanıcımızdan sadece harf, rakam ve alt çizgi kullanabileceği  4 ile 28 karakter arasında kullanıcı adı girmesini istiyoruz ve bunu doğruluyoruz.

```
$kullaniciAdi = "mtRCN4234432_";
if (preg_match('/^[a-z\d_]{4,28}$/i', $kullaniciAdi)) {
echo "kullanıcı adı başarılı!";
}
```

### #2: Telefon Numarası Doğrulama

Kullanıcımızdan (####)### - #### şeklinde telefon numarası girmesini istiyoruz ve bunu doğruluyoruz.

```
$telNo = "(0555)555-5555";
if (preg_match('/^(\(?[0-9]{4}\)?|[0-9]{3,3}[-. ]?)[ ][0-9]{3,3}[-. ]?[0-9]{4,4}$/', $telNo)) {
echo "telefon no başarılı";
}
```

<!--more-->

### #3: E-Posta Doğrulama

Bu sefer kullanıcının @ işaretini ve domain adresini girip girmediğini kontrol ediyoruz.

```
$eMail = "aaa.bbb@ccc.com";
if (preg_match(
'/^[^0-9][a-zA-Z0-9_]+([.][a-zA-Z0-9_]+)*[@][a-zA-Z0-9_]+([.][a-zA-Z0-9_]+)*[.][a-zA-Z]{2,4}$/',
$eMail)) {
echo "e-posta başarılı";
}
```

### #4: IP Adres Doğrulama

Girilen IP adresi ping atmadan doğruluğunu kontrol etmek için

```
$ipAdres = "255.255.255.0";
if (preg_match(
'^(?:25[0-5]|2[0-4]\d|1\d\d|[1-9]\d|\d)(?:[.](?:25[0-5]|2[0-4]\d|1\d\d|[1-9]\d|\d)){3}$',
$ipAdres)) {
echo "ip adresi başarılı";
}
```

### #5: Renk Kodu Doğrulama

Bazen kullanıcımızdan renk kodu girmesini isteyebiliriz.

```
$renk = "#666666";
if (preg_match('/^#(?:(?:[a-f\d]{3}){1,2})$/i', $renk)) {
echo "renk kodu başarılı.";
}
```

### #6: Tarih Doğrulama

Girilen tarihin GG/AA/YYYY formatında olup olmadığına bakıyoruz.

```
$tarih = "10/09/2007";
if (preg_match('/^\d{1,2}\/\d{1,2}\/\d{4}$/', $tarih)) {
echo "tarih başarılı.";
}
```
