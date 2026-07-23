# Kodlama Standartları ve Geliştirici Kuralları

Bu projede yer alan tüm geliştirmeler aşağıdaki kurallara harfiyen uymalıdır. Amaç, sürdürülebilir, güvenli ve performansı yüksek bir yapı kurmaktır.

## 1. Dosya ve Kod Bütünlüğü
- **Tam Dosya Paylaşımı:** Bir dosyada güncelleme yapıldığında, sadece değişen satırlar değil, dosyanın tümü güncel haliyle paylaşılmalı/kaydedilmelidir.
- **Eksiksiz İnceleme:** Projeye dahil edilen veya incelenmesi gereken dosyalar (PHP, SQL, JS) her zaman son satırına kadar okunmalı ve bağlam tamamen anlaşıldıktan sonra işlem yapılmalıdır.

## 2. Veritabanı ve SQL Kuralları
- **Gerçek Veri Şeması:** SQL sorguları yazılırken veya PHP içinde veritabanı işlemleri yapılırken kesinlikle hayali (mock) tablo veya sütun adları üretilmemelidir. Sadece veritabanı şemasında var olan gerçek isimler kullanılmalıdır.
- **Hazırlanmış İfadeler (Prepared Statements):** SQL Injection açıklarını önlemek için tüm veritabanı işlemlerinde PDO ile hazırlanmış ifadeler kullanılmalıdır.

## 3. Bağımlılık ve Dosya Yönetimi
- **Eksik Dosya Kontrolü:** Kodlama sırasında mevcut dosyanın, projede yer alan başka bir sınıf, fonksiyon veya konfigürasyon dosyasına bağımlılığı varsa ve o dosya elinizde yoksa, tahmini kod yazmak yerine eksik dosya doğrudan talep edilmelidir.
- **Modüler Yapı:** Her pazaryeri (örn: TrendyolAPI, AmazonAPI) kendi sınıfı (class) içinde modüler olarak tasarlanmalıdır.

## 4. Hata Yönetimi (Error Handling)
- API entegrasyonlarında dönen hatalar, kullanıcıya doğrudan gösterilmemeli, merkezi ve live(canlı) bir log sistemine (örn: `hata_loglari` tablosu veya dosyası) kaydedilmelidir.
- `try-catch` blokları API isteklerinde zorunludur.

