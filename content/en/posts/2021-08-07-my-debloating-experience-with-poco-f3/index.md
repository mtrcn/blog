---

title: "My debloating experience with Poco F3"
slug: "my-debloating-experience-with-poco-f3"
date: 2021-08-07
tags: 
  - "android"
  - "debloat"
  - "xiaomi"
---

![i01.appmifile.com/webfile/globalimg/MandyZhang/...](images/k11awhitesmall416.png)

I recently bought a Xiaomi Poco F3 (128GB) at £234 from [Xiaomi UK website](https://www.mi.com/uk/). I think it is great hardware at this price. I have been using iPhone for the last three years (XR->11->12). Once I saw this deal on [hotukdeals](https://www.hotukdeals.com/) website, I thought I should give it a try to Android after three years. I knew it will come with a lot of bloatware and I cannot uninstall them in a normal way, but I was ready to deal with it a hard way.

<!--more-->

Before making the final decision for the purchase, I did a quick research on Google and I found some good articles that explain how to remove bloatware on the phone via ADB shell. It seemed straight forward and I decided to purchase the phone.

As soon as I got my phone, I followed these articles and started removing them one by one. However, I made a big mistake and suddenly my phone locked itself. I didn't know that I should remove my phone from my Xiaomi Account before removing the Mi Account application. I had to call Mi Customer Support but they didn't help at all, the guy on the phone asked me to reset my Mi Account password (didn't understand why), once he realized that didn't work, he asked me to send my identification documents to Xiaomi so that they could remove the lock. It was funny because I was removing these applications to stop sharing my personal data. After I did a bit of research on the internet, I found the solution. However, it was definitely annoying.

If you want to debloat your phone, I suggest [this article](https://www.naldotech.com/xiaomi-poco-f3-bloatware/) that explains step by step.

Here is the list of apps that I deleted from my phone.

- com.android.chrome
    - Alternative: [Microsoft Edge](https://play.google.com/store/apps/details?id=com.microsoft.emmx)
- com.android.providers.downloads.ui
- com.android.providers.partnerbookmarks
- com.android.soundrecorder
- com.android.stk
- com.bsp.catchlog
- com.facebook.appmanager
- com.facebook.services
- com.facebook.system
- com.google.android.apps.googleassistant
- com.google.android.apps.messaging
    - Alternative: [QKSMS](https://play.google.com/store/apps/details?id=com.moez.QKSMS)
- com.google.android.apps.subscriptions.red
- com.google.android.apps.wellbeing
- com.google.android.calendar
    
    - Keep it if you use Google Calendar
    
    - Alternative: [Microsoft Outlook](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)
- com.google.android.contacts
    - Keep it if you use Google contacts
    - Alternative: [Simple Contacts](https://play.google.com/store/apps/details?id=com.simplemobiletools.contacts)
- com.google.android.feedback
- com.google.android.gm
    - You may want to keep it if you use GMail
    - Alternative: [Microsoft Outlook](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook)
    - Alternative: [K-9 Mail](https://play.google.com/store/apps/details?id=com.fsck.k9)
- com.google.android.googlequicksearchbox
- com.google.android.inputmethod.latin
    - It is Google Keyboard, you should install an alternative first otherwise it can break your system.
    - Alternative: [Microsoft SwiftKey Keyboard](https://play.google.com/store/apps/details?id=com.touchtype.swiftkey)
- com.google.android.marvin.talkback
- com.google.android.syncadapters.contacts
    - Keep it if you use Google Contacts
- com.mi.android.globalFileexplorer
    - Alternative: [Cx File Explorer](https://play.google.com/store/apps/details?id=com.cxinventor.file.explorer)
- com.mi.android.globalminusscreen
- com.milink.service
- com.mipay.wallet.in
- com.miui.analytics
- com.miui.backup
- com.miui.bugreport
- com.miui.calculator
- com.miui.cleanmaster
- com.miui.cloudbackup
- com.miui.cloudservice
- com.miui.cloudservice.sysbase
- com.miui.daemon
- com.miui.freeform
- com.miui.gallery
    - Alternative: [Simple Gallery Pro](https://play.google.com/store/apps/details?id=com.simplemobiletools.gallery.pro)
- com.miui.hybrid
- com.miui.hybrid.accessory
- com.miui.micloudsync
- com.miui.miservice
- com.miui.mishare.connectivity
- com.miui.msa.global
- com.miui.notes
- com.miui.phrase
- com.miui.player
- com.miui.screenrecorder
- com.miui.screenshot
- com.miui.touchassistant
- com.miui.videoplayer
- com.miui.weather2
- com.miui.wmsvc
- com.miui.yellowpage
- com.tencent.soter.soterserver
- com.xiaomi.account
- com.xiaomi.glgm
- com.xiaomi.joyose
- com.xiaomi.mi\_connect\_service
- com.xiaomi.micloud.sdk
- com.xiaomi.midrop
- com.xiaomi.mipicks
- com.xiaomi.miplay\_client
- com.xiaomi.payment
- com.xiaomi.scanner
- com.xiaomi.simactivate.service
- com.xiaomi.xmsf
- com.xiaomi.xmsfkeeper

As you can see, I put alternatives for some deleted apps because they are essential to read e-mails, browse the internet or your photo gallery. I listed Micorosft alternative for Google applications, you can ignore them if you are dependent on Google services. I mostly use Microsoft applications in my daily routine, so I didn't want to have duplication of the same application from Google.

Unfortunately, this list doesn't cover all installed bloatware because some applications are breaking the phone if you remove them. For example, I couldn't manage to uninstall Security Center, Find Device service, and POCO Launcher. I really wanted to replace POCO Launcher with [my favourite Android launcher](https://play.google.com/store/apps/details?id=com.teslacoilsw.launcher), but it has not been possible so far. When you remove POCO Launcher, it breaks the Recent Apps button's functionality and it stops working. Uninstalling the Security Center application (com.miui.securitycenter) or the Find Device service (com.xiaomi.finddevice) puts the phone in a boot loop.

In addition, when you get a new system update, you may find some uninstalled applications come back, thus I would suggest to keep the list of uninstalled applications to remove them again easily.

I noted some commands below that you may also find useful.

```
# List all installed packages
pm list packages

# List all installed and uninstalled apps
pm list packages -u

# Disable app
pm disable-user app.package.name

# Re-enable it
pm enable app.package.name

# Uninstall app
pm uninstall --user 0 app.package.name

# Install uninstalled app
pm install-existing app.package.name

#Enable ADB via Network
adb tcpip 5555

#Disable ADB Network
adb usb

# Diff Files
# It is usefull to compare output between (pm list packages) and (pm list packages -u), so you can keep the uninstalled apps list easily.
diff --changed-group-format='%>' --unchanged-group-format='' new_packages.txt  all_packages.txt
```
