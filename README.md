# SAVAŞ SİMÜLASYONU: İNSAN İMPARATORLUĞU VE ORK LEJYONU

## 🎯 Proje Amacı
Bu proje, iki ırkın (**İnsan İmparatorluğu** ve **Ork Lejyonu**) savaşını simüle etmek için C dilinde geliştirilmiş bir uygulamadır. Simülasyon, birliklerin temel istatistiklerine, özel kahraman/canavar bonuslarına ve teknolojik araştırma seviyelerine dayanan kapsamlı savaş mekaniklerini içerir. Savaşın durumu bir ızgarada görselleştirilir ve tüm adımlar loglanır.

## 🛠️ Teknolojiler ve Kütüphaneler
* **Dil:** C
* **Görselleştirme:** [raylib](https://www.raylib.com) (20x20 ızgarada görselleştirme için)
* **Dinamik Veri Yükleme:** [curl](https://curl.se) (Senaryo JSON dosyalarını URL'den indirmek için)
* **Veri Formatı:** JSON (Birlik tipleri, kahramanlar, canavarlar, araştırmalar ve senaryolar için)

## ✨ Temel Özellikler ve Mekanikler

### 📊 Veri ve Senaryo Yönetimi
* **Statik Veri Okuma:** Birliklerin temel güçleri, kahramanlar, canavarlar ve araştırma seviyeleri gibi veriler ilgili JSON dosyalarından (`unit_types.json`, `heroes.json`, `creatures.json`, `research.json`) okunur ve C dilindeki `struct` yapılarına manuel olarak ayrıştırılır.
* **Dinamik Senaryo Yükleme:** Kullanıcıdan alınan 1-10 arası bir numara ile URL'den senaryo JSON dosyası indirilir ve birliklerin başlangıç sayıları bu dosyadan sağlanır.
* **Bonuslar:** Kahramanlar, canavarlar ve araştırma seviyeleri, birimlerin saldırı, savunma ve kritik şans değerlerini etkiler.

### ⚔️ Savaş Hesaplamaları
* **Saldırı ve Savunma Gücü:** Birlik başına saldiri/savunma gücü ile birlik sayısının çarpımı ile hesaplanır.
* **Net Hasar:** Rakibin toplam saldırı gücünden, savunan birliğin toplam savunma gücü çıkarılarak hesaplanır.
* **Kritik Vuruş:** Kritik vuruş şansı oranına göre kritik vuruş yapıldığında hasar **1.5 kat** artırılır.
* **Yorgunluk Mekanizması:** Her 5 turda bir, tüm birliklerin saldırı ve savunma güçleri **%10** oranında azalır.
* **Birlik Kayıpları:** Bir birliğin birim başına sağlık durumu sıfıra ulaştığında, o birlik tamamen yok olmuş sayılır.

### 🖥️ Görselleştirme ve Çıktı
* **Raylib Görselleştirme:** Savaş öncesi ve sonrası durumlar $20\times20$ boyutunda bir ızgarada gösterilir. Birliklerin sağlıkları renkli barlarla yansıtılır (Yeşil: %100-%50, Sarı: %50-%20, Kırmızı: %20 ve altı).
* **Detaylı Loglama:** Savaşın her adımı, saldırı/savunma güçlerinin katkıları, verilen net hasarlar ve kalan birim/sağlık bilgileri ile birlikte **`savas_sim.txt`** dosyasına detaylı olarak yazdırılır.

## 🚀 Çalıştırma Talimatları
1.  Projeyi gerekli kütüphaneler (`raylib`, `curl`) ile derleyin.
2.  Uygulamayı çalıştırın.
3.  Komut satırında istenen **1-10 arası bir senaryo numarası** girin.
4.  Açılan Raylib penceresinde savaşı başlatmak için **BOŞLUK (SPACE)** tuşuna basın.
