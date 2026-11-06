JARVIS 12 — Türkçe Sesli Masaüstü Asistanı
Kişisel yapay zekâ destekli Windows masaüstü asistanı. Sesli sohbet, sistem kontrolü, harita, yönetici komutları ve otomatik güncelleme içerir.

Özellikler
Özellik	Açıklama
Sesli sohbet	Gemini Live ile gerçek zamanlı sesli konuşma
Metin arayüzü	Kapsül tabanlı modern arayüz, metin girişi
Sistem kontrolü	Ses, parlaklık, kilitleme, kapatma, pencere işlemleri
Sistem durumu	CPU, RAM, disk, pil, ağ, çalışan uygulamalar
Harita	TomTom SDK ile etkileşimli harita, konum arama, trafik
Uyandırma	"Hey Jarvis" ile sesli uyandırma
Telegram	Bot üzerinden uzaktan komut gönderme
Otomatik güncelleme	GitHub Releases üzerinden canlı sürüm kontrolü ve EXE güncelleme
Kurulum sihirbazı	Windows Asistan kurulum arayüzü (Hoş Geldiniz → Sistem Kontrolü)
Kurulum
Gereksinimler
Windows 10 / 11 (64-bit)
Python 3.8+
İnternet bağlantısı (Gemini API ve güncelleme için)
1. Depoyu klonla / indir
powershell


git clone https://github.com/Emrepromax/WindowsAsistan.git
cd WindowsAsistan
2. Bağımlılıkları kur
powershell


pip install -r requirements.txt
3. API anahtarı al
Google AI Studio adresinden ücretsiz Gemini API anahtarı al.

4. Uygulamayı başlat
powershell


python jarvis_ui.py
İlk açılışta API anahtarı istenir. Kurulum tamamlandıktan sonra uygulama doğrudan açılır.

Kullanım
Ana pencere
F9 (varsayılan): Sesli sohbeti açar/kapatır
Esc: Pencreyi kapatır
Sağ tık: Ayarlar, gizle, çıkış menüsü
Sesli komut örnekleri
"Ses yüzde 50 yap"
"Parlaklığı yüzde 80 yap"
"Ekranı kilitle"
"Bilgisayarı 1 dakika içinde kapat"
"Sistem durumu nedir?"
"İstanbul'da hava nasıl?"
"Haritada Ankara'yı göster"
Ayarlar
Kısayol tuşu değiştirme
Ses tonu seçimi
"Hey Jarvis" uyandırma etkin/devre dışı
Windows başlangıcında otomatik başlatma
Gemini model seçimi
Güncelleme Sistemi
Uygulama GitHub Releases üzerinden canlı güncellemeyi destekler.

Geliştirici için (yayıncı)
Uygulamayı derle:

powershell


pyinstaller --onefile --noconsole --name WindowsAsistan jarvis_ui.py
dist/WindowsAsistan.exe dosyasını GitHub Releases'e yükle:

github.com/Emrepromax/WindowsAsistan/releases
Yeni sürüm etiketi: v1.0.0, v1.1.0 gibi
EXE dosyasını asset olarak ekle
Kullanıcılar uygulama açıldığında otomatik olarak yeni sürüm bilgisi alır ve güncelleyebilir.

SHA-256 (isteğe bağlı, önerilen)
Güvenli güncelleme için manifest.json dosyası oluşturulabilir:

json


{
  "version": "1.0.0",
  "download_url": "https://github.com/Emrepromax/WindowsAsistan/releases/download/v1.0.0/WindowsAsistan.exe",
  "sha256": "dosyanin_sha256_hashi",
  "release_notes": "Sürüm notları buraya yazılır",
  "published_at": "2026-01-01T00:00:00Z",
  "asset_name": "WindowsAsistan.exe"
}
SHA-256 hash almak için:

powershell


Get-FileHash WindowsAsistan.exe -Algorithm SHA256
Proje Yapısı
Code block


Jarvis V1 - Kopya/
├── jarvis_ui.py              # Giriş noktası
├── jarvis/
│   ├── __init__.py           # Sürüm bilgisi (12.0.0)
│   ├── app.py                # Ana uygulama yöneticisi
│   ├── launcher.py           # Başlatıcı (splash + onboarding)
│   ├── config.py             # Ayarlar ve API anahtarı
│   ├── update_config.py      # GitHub güncelleme yapılandırması
│   ├── updater.py            # Güncelleme çekirdeği
│   ├── paths.py              # Dosya yolları
│   ├── core/                 # Temel mantık (agent, speech, logger)
│   ├── brain/                # Beyin (planner, sanitizer, prompts)
│   ├── executor/             # İşlemciler (sistem, media, apps, vb.)
│   ├── ui/                   # Arayüz (pencere, tema, splash, ayarlar)
│   ├── workers/              # Arka plan işleri (boot, wake word, komut)
│   ├── models/               # AI modelleri ve router
│   ├── memory/               # Hafıza ve veritabanı
│   ├── audio/                # Ses girişi/çıkışı
│   ├── gemini/               # Gemini istemcisi
│   └── integrations/         # Telegram entegrasyonu
├── installer/
│   ├── setup_core.py         # Kurulum sisteminin çekirdeği
│   ├── main.py               # Kurulum arayüzü giriş noktası
│   └── ui/                   # Kurulum penceresi (hoş geldiniz, sistem kontrolü)
├── assets/
│   └── windows_asistan_logo.png  # Uygulama logosu
├── requirements.txt          # Python bağımlılıkları
├── config.json               # Kullanıcı ayarları (oluşturulur)
└── README.md                 # Bu dosya
Sorun Giderme
Sorun	Çözüm
"API anahtarı gerekli"	Google AI Studio'dan anahtar alıp ayarlara girin
Güncelleme butonu devre dışı	update_config.py'de GITHUB_REPO ayarlanmalı
Mikrofon çalışmıyor	Ayarlar → Mikrofon cihazını seçin
Uygulama açılmıyor	python jarvis_ui.py ile konsolda çalıştırıp hatayı kontrol edin
"Jarvis zaten çalışıyor"	Görev yöneticisindeki eski işlemi sonlandırın
Lisans
Bu proje kişisel kullanım için geliştirilmiştir.
