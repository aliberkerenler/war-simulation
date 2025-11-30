#SAVAŞ SİMÜLASYONU: İNSAN İMPARATORLUĞU VE ORK LEJYONU (C)#

📝 Proje Tanımı
Bu proje, İnsan İmparatorluğu ve Ork Lejyonu arasındaki epik bir savaşı simüle eden bir C dilinde yazılmış uygulamadır. Simülasyon, birliklerin temel istatistiklerini, kahramanların bonuslarını, canavarların etkilerini ve araştırma seviyelerinin geliştirmelerini dinamik olarak hesaba katar. Savaş, Raylib kütüphanesi ile görselleştirilmiş bir 20x20 ızgarada adım adım ilerler ve tüm süreç detaylıca bir metin dosyasına kaydedilir.

🛠️ Teknolojiler ve Kütüphaneler
Dil: C

Görselleştirme: raylib (Grafik ve 20x20 ızgara çizimi için)

Dinamik Veri Yükleme: curl (Senaryo JSON dosyalarını URL'den indirmek için)

Veri Formatı: JSON (Birlik tipleri, kahramanlar, canavarlar, araştırmalar ve senaryolar için)

✨ Temel Özellikler ve Mekanikler
Birlik ve Geliştirme Yönetimi
Statik Veri Okuma: Birliklerin temel saldırı/savunma/sağlık/kritik şans değerleri ve kahraman/canavar/araştırma detayları JSON dosyalarından (unit_types.json, heroes.json, creatures.json, research.json) manuel olarak ayrıştırılarak belleğe alınır.

Dinamik Senaryo Yükleme: Kullanıcıdan alınan 1-10 arası bir numara ile ilgili URL'den senaryo JSON dosyası indirilir ve birliklerin başlangıç sayıları buradan alınır.

Bonus Hesaplamaları: Kahramanlar, canavarlar ve araştırma seviyeleri, ilgili birimlere saldırı, savunma ve kritik şans bonusları ekler.

Savaş Mekanikleri
Saldırı ve Savunma Hesaplaması:

Saldırı Gücü = Birlik Başına Saldırı Gücü × Birlik Sayısı

Savunma Gücü = Birlik Başına Savunma Gücü × Birlik Sayısı

Net Hasar Hesaplaması: Net Hasar = Saldırı Gücü × (1 - (Karşı Birliğin Savunma Gücü / Kendi Saldırı Gücü))

Kritik Vuruş: Kritik şans oranına göre kritik vuruş yapıldığında hasar 1.5 kat artar.

Sağlık ve Birlik Yok Olması: Birliğin sağlığı (birim başına) net hasara orantılı olarak azaltılır. Sağlığı sıfırın altına düşen birimler savaş dışı kalır.

Yorgunluk Mekanizması: Her 5 turda bir, tüm birliklerin saldırı ve savunma güçleri %10 oranında azalır.

Görselleştirme ve Çıktı
Görsel Simülasyon: Savaş öncesi ve sonrası durumlar 20x20'lik bir ızgarada görselleştirilir. Her hücrede maksimum 100 birim bulunur.

Sağlık Durumu Görseli: Birliklerin sağlık durumları renkli barlarla gösterilir:

Yeşil: %50 ve üzeri Sağlık

Sarı: %20 - %50 arası Sağlık

Kırmızı: %20 ve altı Sağlık

Detaylı Savaş Logu: Savaşın her adımı, hesaplanan saldırı/savunma güçleri, verilen net hasar ve kalan birim/sağlık bilgileri ile birlikte savas_sim.txt dosyasına detaylı olarak yazılır.

🚀 Çalıştırma Talimatları
Projeyi Raylib ve cURL kütüphanelerini içerecek şekilde derleyin.

Uygulamayı çalıştırın.

Komut satırında istenen 1 ile 10 arasında bir senaryo numarası girin.

Simülasyon başlayacak ve Raylib penceresinde görselleştirme görüntülenecektir.

Savaşı başlatmak için Raylib penceresi açıkken BOŞLUK (SPACE) tuşuna basın.
