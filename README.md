# E-Ticaret ve Pazaryeri Entegrasyon Sistemi

Bu proje, farklı e-ticaret altyapıları (Woocommerce) ve pazaryerleri (Trendyol, Hepsiburada, N11, Amazon, İdefix, Pazarama, PTTAvm vb.) arasında ürün, stok, fiyat ve sipariş, iade & değişim ve soru cevap yanıtlama senkronizasyonunu sağlayan merkezi bir entegrasyon yazılımıdır.

## 🚀 Özellikler
- **Çift Yönlü Senkronizasyon:** Pazaryerinden sipariş çekme, e-ticaret sitesine aktarma.
- **Stok ve Fiyat Yönetimi:** Tek merkezden tüm platformlardaki stok ve fiyatları güncelleme.
- **Kategori ve Özellik Eşleştirme:** Platformlar arası farklı kategori ağaçlarını eşleştirme.
- **Loglama ve Hata Yönetimi:** API isteklerinin ve senkronizasyon hatalarının takibi.

## 🛠️ Sistem Gereksinimleri
- PHP >= 8.2
- MySQL >= 8.0 veya MariaDB >= 10.5
- Cron Job desteği (Zamanlanmış görevler için)
- Gerekli PHP eklentileri: `cURL`, `JSON`, `PDO`, `mbstring`

