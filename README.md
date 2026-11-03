# Ses Defteri (Android)

Klasörlü ses kaydedici. Kayıtlar telefonda saklanır, iç içe klasör açılır, dinleme hızı 0.25× ile 5× arasında 0.01 hassasiyetle ayarlanır.

Uygulama `www/index.html` dosyasındadır ve Capacitor ile Android uygulamasına paketlenmiştir. Mikrofon izni (`RECORD_AUDIO`) eklidir; ilk kayıtta Android izin sorar.

## Yol 1: GitHub ile APK al (bilgisayarda Android Studio gerekmez)

1. github.com'da ücretsiz bir hesap aç, yeni bir **boş depo** oluştur (adı: `ses-defteri`).
2. Bu klasörün içindekileri depoya yükle. Web arayüzünde **Add file > Upload files** ile klasörün içindeki her şeyi (`.github` ve `android` klasörleri dahil) sürükleyip bırakabilirsin. Toplam 70 dosya kadardır, GitHub'ın tek seferde 100 dosya sınırının altında kalır. Mac'te `.github` klasörü gizli görünür; Finder'da `Cmd + Shift + .` ile gizli dosyaları göster.
3. Depoda **Actions** sekmesine gir. "APK derle" iş akışı kendiliğinden başlar (başlamazsa **Run workflow** düğmesine bas).
4. 5-10 dakika sonra iş akışı yeşil olunca çalıştırmanın sayfasının altındaki **Artifacts** bölümünden `ses-defteri-apk` dosyasını indir. Zip'in içinde `app-debug.apk` vardır.
5. APK'yı telefona aktar ve aç. Android "bilinmeyen kaynaklardan kurulum" izni isteyecek; izin verip kur.

## Yol 2: Android Studio ile

1. Android Studio'yu kur, **Open** ile bu klasörün içindeki `android` klasörünü aç.
2. Gradle eşitlemesi bitince **Build > Build APK(s)** de.
3. APK `android/app/build/outputs/apk/debug/app-debug.apk` yoluna çıkar.

İstersen telefonu USB ile bağlayıp doğrudan **Run** da diyebilirsin.

## Uygulamayı değiştirmek

Arayüz ve davranış `www/index.html` içindedir. Değiştirdikten sonra `npm install` ve `npx cap sync android` çalıştırıp yeniden derle (GitHub kullanıyorsan dosyayı yüklemen yeterli).

## Notlar

- Üretilen APK "debug" imzalıdır; kendi telefonunda kullanmak için yeterlidir. Play Store'a koymak için ayrıca imzalı sürüm gerekir.
- Kayıtlar uygulamanın kendi verisinde durur. Uygulamayı silersen kayıtlar da silinir.
- Yazı tipleri ilk açılışta internetten indirilir; internet yoksa sistem yazı tipi kullanılır, uygulama yine çalışır.
