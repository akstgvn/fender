# İstatistik Mobil Uygulaması Taslak Projesi

Bu belge, lise öğrencilerinin TÜBİTAK 2204-A kapsamında araştırma verilerini kolayca analiz etmelerini sağlayacak istatistik odaklı bir mobil uygulama için proje taslağını özetler.

## Amaç
- SPSS veya benzeri masaüstü yazılımlara ihtiyaç duymadan temel istatistiksel analizleri mobil ortamda sunmak.
- Ön test-son test karşılaştırmaları, temel betimsel istatistikler ve yaygın parametrik / parametrik olmayan testleri hızlı şekilde uygulamak.
- Öğrencilere adım adım yönlendirmeler ve örnek çıktı yorumları sağlayarak raporlama sürecini kolaylaştırmak.

## Hedef Kullanıcılar
- TÜBİTAK 2204-A için proje yürüten lise öğrencileri.
- Basit arayüzle veri girişi ve sonuçları anlamlandırmak isteyen öğretmen/rehberler.

## Ana Özellikler
1. **Betimsel İstatistikler**: Ortalama, medyan, mod, varyans, standart sapma, yüzde, çeyrekler arası aralık.
2. **Karşılaştırma Testleri**:
   - Bağımlı örneklemler t-testi (ön test / son test).
   - Bağımsız örneklemler t-testi (iki grup karşılaştırması).
   - Tek yönlü ANOVA ve post-hoc (Tukey) desteği.
   - Wilcoxon işaretli sıra testi ve Mann-Whitney U (parametrik olmayan alternatifler).
3. **Korelasyon**: Pearson ve Spearman korelasyonları.
4. **Görselleştirme**: Histogram, kutu grafiği, dağılım grafiği ve hata çubukları.
5. **Veri Girişi Kolaylığı**:
   - Elle tablo girişi, CSV içe aktarma.
   - Küçük örnek veri setleriyle öğrenme modu.
6. **Raporlama**:
   - Otomatik APA formatına yakın özetler (test istatistiği, serbestlik derecesi, p-değeri, etki büyüklüğü).
   - PDF/Word’e aktarma veya paylaşım.
7. **Rehberli İş Akışları**: Test seçimi için soru-cevap asistanı (ör. ölçek türü, grup sayısı, dağılım varsayımı).
8. **Gizlilik**: Cihaz üzerinde hesaplama ve isteğe bağlı yerel şifreli depolama.

## Teknoloji Seçimi
- **Çapraz Platform**: Flutter (Dart) veya React Native (TypeScript) ile Android/iOS desteği.
- **İstatistik Motoru**: 
  - Flutter için `statistics` veya `basic_utils` paketleri + özel hesaplamalar.
  - React Native için `simple-statistics` veya Python temelli mikro servis (ör. Pyodide/wasm) seçeneği.
- **Durum Yönetimi**:
  - Flutter: Riverpod/Bloc.
  - React Native: Redux Toolkit/Zustand/Recoil.
- **Grafikler**: `charts_flutter` veya `react-native-svg` + `victory-native`.
- **Dokümantasyon/Raporlama**: `pdf` (Flutter) veya `react-native-pdf` ile rapor çıktıları.

## Basit Mimari Şeması
- **UI Katmanı**: Formlar, tablo girişi, grafik bileşenleri.
- **İş Kuralları**: Test seçici, varsayım kontrolleri (ör. normal dağılım, varyans homojenliği) için doğrulama katmanı.
- **İstatistik Servisi**: Hesaplama fonksiyonları; giriş doğrulama ve hata mesajları.
- **Veri Katmanı**: Yerel depolama (SQLite veya cihaz dosyası), CSV içe/dışa aktarma.

## Örnek Kullanıcı Akışı (Flutter)
1. **Proje Oluştur**: İsim, araştırma sorusu ve değişken türlerini seç.
2. **Veri Ekle**: Grup/ölçüm bazlı tablo girişi veya CSV yükleme.
3. **Test Seçimi**: Uygulama; veri tipi (sürekli/kategorik), grup sayısı, bağımlı/bağımsız bilgisine göre öneri sunar.
4. **Analiz**: Sonuçlar kartlarda gösterilir; test istatistiği, p, serbestlik derecesi, etki büyüklüğü (Cohen’s d, eta kare). Gereken varsayım sağlanmıyorsa uyarı ve alternatif test önerisi.
5. **Görselleştir**: Otomatik grafikler + özelleştirme.
6. **Raporla**: PDF/Word çıktısı; kaynakça/yorum alanları.

## Temel İstatistik Fonksiyonları (örnek)
- Ortalama: \( \bar{x} = \frac{1}{n} \sum x_i \)
- Varyans (örnek): \( s^2 = \frac{1}{n-1} \sum (x_i - \bar{x})^2 \)
- Standart sapma: \( s = \sqrt{s^2} \)
- Cohen’s d (bağımsız gruplar): \( d = \frac{\bar{x}_1 - \bar{x}_2}{s_{pooled}} \)
- t-testi, ANOVA, korelasyon ve parametrik olmayan testler için hazır paketler kullanılabilir; sonuçlar APA benzeri formatta sunulur.

## Varsayım Kontrolleri
- **Normal Dağılım**: Shapiro-Wilk testi ve histogram/Q-Q plot yorumları.
- **Varyans Homojenliği**: Levene testi.
- **Aykırı Değer Uyarıları**: IQR kuralı veya Z-skoru (|z| > 3).
- Varsayımlar sağlanmazsa otomatik olarak uygun parametrik olmayan test önerisi (ör. t yerine Wilcoxon veya Mann-Whitney).

## Güvenlik ve Etik
- Veriler cihazda şifrelenmiş olarak saklanabilir (ör. AES + platform secure storage).
- İnternet bağlantısı gerektirmeden çalışacak çevrimdışı mod.
- Paylaşım yapılırken kişisel veri maskeleme uyarıları.

## Yol Haritası (Öneri)
- **Hafta 1-2**: İhtiyaç analizi, arayüz kabloları (wireframe), teknoloji seçimi.
- **Hafta 3-4**: Veri modeli ve istatistik modülünün temel fonksiyonları (betimsel istatistik, t-testleri).
- **Hafta 5-6**: ANOVA, parametrik olmayan testler, grafikler.
- **Hafta 7**: Raporlama modülü (PDF/Word), paylaşım.
- **Hafta 8**: Kullanılabilirlik testi, hata düzeltme, dokümantasyon ve sunum hazırlığı.

## Sunum ve Değerlendirme Önerileri
- Kısa bir demo videosu: Veri girişi → test seçimi → sonuç/rapor.
- Varsayım kontrollerinin ve etik/gizlilik özelliklerinin vurgulanması.
- Örnek bir lise projesi datasıyla analiz senaryosu (ön test/son test örneği) gösterilmesi.

Bu taslak, uygulamayı hayata geçirirken proje raporu, iş planı ve demo hazırlığı için temel bir referans sağlar.
