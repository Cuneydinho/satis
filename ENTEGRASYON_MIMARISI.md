# Entegrasyon ve Mimari Yapı

Bu döküman, pazar yerleri ile e-ticaret siteleri arasındaki veri akışını ve periyodik işlemleri tanımlar.

## 🔄 Veri Akışı (Data Flow)
1. **Ürün Kaynağı:** Ana veri kaynağı (Master Data) e-ticaret sitesinin veritabanıdır.
2. **Kuyruk (Queue) Sistemi:** Çok sayıda ürün güncellendiğinde, pazaryeri API limitlerine (Rate Limit) takılmamak için işlemler veritabanında bir kuyruk tablosuna alınır.

## ⏱️ Zamanlanmış Görevler (Cron Jobs)
Sistemdeki senkronizasyon işlemleri aşağıdaki periyotlarla çalışacak şekilde ayarlanmalıdır:

- `cron_orders.php` (Her 5 dakikada bir): Pazaryerlerinden yeni siparişleri çeker ve sisteme yazar.
- `cron_stocks.php` (Her 15 dakikada bir): E-ticaret sitesinde stoğu/fiyatı değişen ürünleri tespit edip ilgili pazaryerlerine API isteği atar.
- `cron_products.php` (Günde 1 kez): Toplu ürün aktarımı ve eksik ürünlerin kontrolünü yapar.

## 🔐 Güvenlik ve API Limitleri
- Pazaryerlerinin belirlediği anlık istek sınırları (Rate Limits) kesinlikle aşılmamalıdır. Sistem gerekirse `sleep()` fonksiyonu veya kuyruk gecikmesi ile kendini yavaşlatmalıdır.
- API anahtarları, Secret Key'ler ve veritabanı şifreleri veritabanında veya dosya sisteminde şifrelenmiş (encrypted) şekilde tutulmalıdır.

## - Ürün havuzları (Product Pool)

- Bir adet Master Ürün havuzu, ayrıca her pazaryeri ve satış platformunun kendine ait bir ürün havuzu olmalıdır. Eğer ki kullanıcı bir pazaryerinde bir ürünün satışa açıyorsa İlgili ürün Master ürün havuzundan Pazaryerleri ve Eticaret havuzlarına düşmelidir. Şu şekilde telaffuz edilecektir. 

a- Master Ürün Havuzu
b- Amazon Ürün Havuzu
c- Trendyol Ürün Havuzu
d- Hepsiburada Ürün Havuzu
e- N11 Ürün Havuzu
f- İdefix Ürün Havuzu
g- Pazarama Ürün Havuzu
h- PTTAvm Ürün Havuzu
i- WooCommerce Ürün Havuzu

Master Ürün Havuzu liste ekranında Seçililere toplu işlemler yapmaya imkan sağlanmalıdır, Örneğin : Seçili ürünleri toplu olarak Fiyat değiştir, Kategori eşle, Pazaryerlerinde Satışa Aç/Kapat, Stokları Güncelle, Fiyatları Güncelle gibi. (Bunu daha sonra geliştireceğiz)

- Yüklemeler (Uploads)
- Ürün görselleri yada başka bir görsel yükleme ihtiyacı olduğunda bunu galeriden seçmeme izin ver, gorsellerin dosya adlarını, hangi ürüne ekliyorsam o ürünün ismiyle rename yapalım. Ortak görselleri tekrar tekrar upload etmek yerine ortak görselleri kullanmak için Görsel galeri havuzundan seçerek sunucuda gereksiz yer kaplamanın önüne geçelim. 

- Güvenlik ve Giriş
- Bir kullanıcı giriş denetim sistemine sahip olmalı. Login ekranından Kullanıcı adı şifre ve yetkilendirmeye sahip olmalı. Stok kartları, Siparişler, İadeler Parametreler, Ayarlar gibi bölümleri ayrıştırarak Yetkilendirme rolü belirleyerek, Kullanıcı bazında (Görüntüleme	Ekleme	Düzenleme	Silme) yetkilerini ayrıştıralım.

- Bilgilendirme 
 15dakikalık sorgularla Sipariş, İade, Soru Cevap modüllerinden trigger olacak şekilde kullanıcılara notofication ve sesli bildirim oluşturalım.

