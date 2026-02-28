---
title: "PHP ile Türkçe HTML yada Metin e-posta göndermenin en kolay yolu"
slug: "php-ile-turkce-html-yada-metin-e-posta-gondermenin-en-kolay-yolu"
date: 2009-05-06
---

![swift mailer](images/logo.png "swift mailer")

Bir süredir Proje Takip Sistemi kurmaya çalışıyorum. Kendim oturup bir sistem yazmak yerine kolay yolu seçip hazır yapılmışları tek tek inceledim ve basit ve işlevsel [WebCollab](http://webcollab.sourceforge.net/)'ı kullanmaya karar verdim.

Ancak ne zaman hazır bir şey kullanmak istersem mutlaka bir problem çıkıyor. Webcollab'ın kendi fonksiyonlarıyla Türkçe karakterli(UTF-8 veya ISO) ne HTML nede salt metin e-postaları istediğim gibi gönderemedim. Kodlar ile bir süre uğraştıktan sonra artık yeniden teker icat etmeye başladığımı fark edince hazır bir e-posta kütüphanesi kullanmak için ufak bir araştırma yaptım ve [Swift Mailler](http://swiftmailer.org) ile karşılaştım. WebCollab'ın kendi kütüphanesini tamamen silerek [Swift Mailler](http://swiftmailer.org) ile çalışabilir olarak programladım. Neyse ki istediğim gibi sistem sorunsuz çalışmaya başladı.

**Nasıl Yaptım?**

<!--more-->

Bunun için Swift Mailler'ın dokümantasyonunu okumanız yeterli, istediğiniz PHP 5 uygulamasına entegre edebilirsiniz. Ben size WebCollab'a nasıl entegre ettiğimi açıklayacağım.

1. Swift Mailler'ın [güncel versiyonunu indirin](http://swiftmailer.org/download).
2. Sıkıştırılmış dosya içinden **lib** klasörünü bir yere çıkarıp adını **mail\_lib** olarak değiştirin.
3. Bu klasörü WebCollab uygulamasının bulunduğu yerdeki **includes** klasörünün altına koyun.
4. Yine includes altında email.php dosyasını açın. İçeriğini tamamen temizleyerek aşağıdaki kodu yerşeltirip yükleyin. Artık sorun kalmayacaktır.

```

//security check
if(! defined('UID' ) ) {
  die('Direct file access not permitted' );
}

//includes
require_once(BASE.'includes/admin_config.php' );

//
// Email sending function
//

function email($to, $subject, $message ) {

  if(USE_EMAIL === 'N' ) {
    //email is turned off in config file
    return;
  }
  if(sizeof($to) == 0  ) {
    //no email address specified - end function
    return;
  }
  require_once(BASE.'includes/mail_lib/swift_required.php' );

  $transport = Swift_MailTransport::newInstance();
  $mailer = Swift_Mailer::newInstance($transport);
  $mail = Swift_Message::newInstance()
  ->setSubject($subject)
  ->setFrom('posta@posta.com') //bu satıra kendi e-posta adresinizi yazın.
  ->setTo((array)$to)
  ->setBody($message);
  $mailer->send($mail);
}

?>

```
