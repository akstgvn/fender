# fender

Bu depo şu anda yalnızca **İstatistik Mobil Uygulaması** için proje taslağını içerir. Çalıştırılabilir bir mobil uygulama kodu henüz eklenmedi. Aşağıdaki adımlar, geliştirmeye başlamak ve bir prototip çalıştırmak için yol gösterir.

## Başlangıç Durumu
- Kod yok; sadece `PROJE.md` içinde gereksinimler ve yol haritası bulunuyor.
- Hedef: Flutter veya React Native ile Android/iOS üzerinde istatistik analizlerini yapan bir mobil uygulama geliştirmek.

## Flutter ile hızlı prototip
1. Flutter SDK'yı kurun: [Flutter kurulumu](https://docs.flutter.dev/get-started/install).
2. Yeni proje oluşturun:
   ```bash
   flutter create istatistik_app
   cd istatistik_app
   ```
3. Paket örnekleri:
   - İstatistik: `statistics` paketi veya özel hesaplamalar.
   - Grafikler: `charts_flutter` veya `fl_chart`.
4. Geliştirme ve çalıştırma:
   ```bash
   flutter pub add statistics fl_chart
   flutter run
   ```
5. `lib/` altında veri girişi ekranı, test seçici ve rapor bileşenlerini ekleyerek `PROJE.md`deki akışı uygulayın.

## React Native alternatifi
1. Kurulum: Node.js ve Watchman sonrası
   ```bash
   npx react-native init istatistikApp
   cd istatistikApp
   ```
2. Paket örnekleri:
   - İstatistik: `simple-statistics`.
   - Grafikler: `victory-native` veya `react-native-svg` tabanlı çözümler.
3. Geliştirme ve çalıştırma:
   ```bash
   npm install simple-statistics victory-native react-native-svg
   npx react-native start
   npx react-native run-android   # veya run-ios
   ```
4. `PROJE.md`deki kullanıcı akışına göre ekranlar ve test hesaplamalarını ekleyin.

## Depoyu kullanırken
- Henüz çalıştırılacak bir şey yok; önce yukarıdaki adımlarla bir çatı proje kurup `PROJE.md`deki gereksinimleri kodlayın.
- Geliştirme ilerledikçe bu depoya kaynak kodu ve yönergeler ekleyebilirsiniz.

## İlgili doküman
- Ayrıntılı proje taslağı: [PROJE.md](./PROJE.md)
