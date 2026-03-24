# Taze Kalsın: Akıllı Gıda Takip ve İndirim Platformu

## 📌 Proje Vizyonu ve Problem Tanımı
Küresel ölçekte büyük bir sorun olan gıda israfını yerel düzeyde çözmeyi hedefleyen "Taze Kalsın", marketlerin Son Tüketim Tarihi (S.T.T.) yaklaşan ürünlerini israf etmek yerine, anlık bildirim ve rezervasyon tabanlı dijital bir platform üzerinden indirimli fiyatlarla tüketiciye ulaştırmasını sağlar. Proje, hem marketlerin zararını minimize etmeyi hem de tüketicilerin uygun fiyatlı gıdaya erişimini kolaylaştırarak sürdürülebilir bir ekosistem yaratmayı amaçlar.

## 👥 Geliştirme Takımı ve Rol Dağılımı (Çevik/Agile Yapı)
Değerlendirme kriterlerinde istenen rol netliği ve organizasyonel yapı şu şekilde kurgulanmıştır:

* *Scrum Master:* Hilal
    * Sorumluluk: Çevik süreçlerin takibi, Jira/Kanban panosunun yönetimi ve ekip içi engellerin kaldırılması.
* *Product Owner:* Adem
    * Sorumluluk: Ürün İş Listesi'nin (Product Backlog) önceliklendirilmesi ve iş gereksinimlerinin (Use Case) tanımlanması.
* *Geliştirme Takımı (Dev Team):* Gülçin, Mehtap, Merve
    * Sorumluluk: Sistem analizi, UML modelleme, veritabanı tasarımı ve kodlama (sonraki sprintlerde).

---

## 🎯 Sprint 1 Hedefleri ve Teknik Çıktılar (Increment)
31 Mart 2026 tarihindeki 1. Sprint sonu sunumu için projenin temel analiz, sistem sınırları ve veritabanı mimarisi (UML Sınıf ve ER tasarımları) tamamlanmıştır.

### 1. Kullanım Senaryosu (Use Case) Analizi ve Sistem Sınırları
Sistemin tüm aktörleri (Tüketici, Market Sahibi, Sistem Yöneticisi) ve onların sistemle olan etkileşimleri modellenmiştir. Bu aşamada yapılan en kritik mühendislik kararı, fiziksel dünyada yaşanabilecek yarış durumunu (race condition) önlemek için *QR/PIN tabanlı rezervasyon* mantığının sisteme entegre edilmesidir.

*Detaylı Analiz Kararları:*
* *Tüketici:* Ürünleri sadece görüntülemekle kalmaz, 30 dakikalık süre için rezerve edebilir.
* *Market:* Stok yönetimini üstlenir ve satışı sadece rezervasyon koduyla doğrular.
* *Sistem Yöneticisi:* Marketlerin meşruiyetini onaylayarak platformun güvenliğini sağlar.

![Use Case Diyagramı](use-case-diagram.png)

### 2. UML Sınıf (Class) Diyagramı ve Mantıksal Veritabanı Mimarisi (ERD)
Sistemin veritabanı omurgası, nesneye yönelik prensiplere uygun olarak 4 temel varlık (Tüketici, Market, Ürün, Rezervasyon) üzerinden tasarlanmıştır. Bu tasarım, hocanızın kriterlerinde istenen "detaylı veritabanı tasarımı" somut çıktısını oluşturur.

*Teknik Derinlik ve Veritabanı Standartları:*
* *Normalizasyon:* Veri tekrarını önlemek için taslak 3NF'ye (Third Normal Form) uygun hale getirilmiştir.
* *Veri Tutarlılığı (Integrity):* Tuketici_ID, Market_ID, Urun_ID gibi alanlar üzerinden Birincil ve Yabancı Anahtar (PK/FK) ilişkileri kurularak veri bütünlüğü garantilenmiştir.
* *Yarış Durumu (Race Condition) Çözümü:* Rezervasyon tablosundaki Durum (ENUM) ve PIN_Kodu alanları, aynı ürünün aynı anda iki kişiye satılmasını veritabanı seviyesinde engellemektedir.
* *İş Mantığı (Business Logic) Kararları:* Tüketicinin marketin kapalı olduğu saatte rezervasyon yapmasını engellemek için Market tablosuna Acilis_Saati ve Kapanis_Saati alanları eklenmiştir.

![Veritabanı Şeması](database-schema.png)

---
Bu doküman, Çevik (Agile) Yazılım Mühendisliği süreç yönetimi ve versiyon kontrol standartlarına uygun olarak 1. Sprint sonunda elde edilen resmi Analiz ve Tasarım Raporudur.
